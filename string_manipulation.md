### 살펴볼 명령어: length, lower, strpos, substr, subinstr, trim, split

```stata
help string_functions

length(s)
length("ab") = 2

lower(s)
lower("THIS") = this

strpos(s1,s2)
strpos("this","is") = 3

substr(s,n1,n2)
substr("abcdef",2,3) = "bcd”

subinstr(s1,s2,s3,n)
subinstr("this is this","is","X",.) = "thX X thX“

trim(s)
trim(" this ") = "this“

wordcount(s)
wordcount("Global Economics in SKKU") = 4
```

<br>

### Regular expression in Stata
```
regexm(s,re)
regexr(s1,re,s2)

sysuse auto
list make if regexm(make, "^B") == 1
list make if regexm(make, "ck") == 1
list make if regexm(make, "[0-9]$") == 1
```

<br>

### 활용 사례: 심평원 의료기관 현황 분석에 사용된 코드 샘플
```stata
gen temp=address
split temp, p("(")
split temp2, p(,)
replace temp21=subinstr(temp21,")","",.)
rename temp21 dong
order dong, before(address)
split dong, p(.)

split address
rename address1 region
rename address2 district
gen d_focus=(strpos(name,"성형")>0)
```

***

### Further references for regular expression in Stata
- [Source 1 정규표현식 관련 블로그 글](http://dreamingpeace.tistory.com/57)
- [Source 2 Stata.com](http://www.stata.com/support/faqs/data-management/regular-expressions/)
- [Source 3 Regular Expressions for Dummies](http://soc596.blogspot.kr/)



