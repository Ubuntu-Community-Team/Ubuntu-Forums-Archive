---
title: "aptitude search patterns don't work"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by doru001 on 2009-08-13
I just installed Ubuntu Server 8.04.3 LTS and aptitude refuses to search anything but shorthands:

```
$ aptitude search "?name(apt)"
E: Regex compilation error: Invalid preceding regular expression
$ aptitude search ~napt
p   add-apt-key                          - Command line tool to add GPG keys to the APT ke
i   apt                                  - Advanced front-end for dpkg
p   apt-build                            - frontend to apt to build, optimize and install
[...]

```Anyone can reproduce this?

---

### Post by dstew on 2009-08-13
I am not too sure about this, but the pattern in the search command doesn't seem to have the correct syntax. You can search for a name, or part of a name, but the quotation mark is being interpreted as part of a file name. Is this what you intended? If the quotation mark is part of a file name, it needs to be escaped in the search command argument. See [this document]("http://olympus.het.brown.edu/cgi-bin/dwww?type=file&location=/usr/share/doc/aptitude/README"), find the section on "Search Patterns".

Even though a file name can have any characters, even question marks or quote marks, you have to be careful when you use these characters in a command. For example, the bash shell interprets the question mark as a "wild card", and will return files with any character in that place. If your file name has a question mark in it, however, you need to create a special argument for bash commands that escapes the quote mark. This tells the shell to treat the quote mark as a real file name character, and not as a wild card. I think something similar is happening here. The aptitude search parser (using regex) hit the quote mark, and this character is not allowed in its parsing rules, unless it is escaped. Anyway, have a look at the document.

---

### Post by doru001 on 2009-08-13
> **dstew said:**
> I am not too sure about this, but the pattern in the search command doesn't seem to have the correct syntax. 
```
# aptitude search ?name(apt)
-bash: syntax error near unexpected token `('

```Thanks for your answer. Just tell me what is the correct syntax for a search pattern. How can I search for apt as part of a name if I want to use search patterns, but not shorthands. So what is the equivalent non shorthand for the: 
```
aptitude search ~napt 
```shorthand?

---

### Post by dstew on 2009-08-13
I am not sure what you are asking. What do you mean by non-shorthand? Give me an example. Do you mean patterns that are used in other programs to perform searches? I am not sure that the same patterns will work in any program. For example, patterns that work in bash will not work in aptitude search.

---

### Post by doru001 on 2009-08-14
> **dstew said:**
> I am not sure what you are asking. What do you mean by non-shorthand? Give me an example. Do you mean patterns that are used in other programs to perform searches? I am not sure that the same patterns will work in any program. For example, patterns that work in bash will not work in aptitude search.
Sorry, I realised too late that we don't have a common context. In aptitude, Search Patterns are defined here: 
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03.html]("http://algebraicthunk.net/%7Edburrows/projects/aptitude/doc/en/ch02s03s01.html")
and Shorthands here: 
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s02.html]("http://algebraicthunk.net/%7Edburrows/projects/aptitude/doc/en/ch02s03s02.html")
A complete list is here: 
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html]("http://algebraicthunk.net/%7Edburrows/projects/aptitude/doc/en/ch02s03s05.html")

Please check if you can run any Search Pattern, like: 
```
aptitude search ?name(apt)
```or you can run only shorthands, like: 
```
aptitude search ~napt
```Thanks for your answers.

---

### Post by dstew on 2009-08-15
Yes, I get the same behavior as you do. In response to the aptitude search query:```
donn@donn-desktop:~$ aptitude search ?name(apt)
bash: syntax error near unexpected token `('
```When I remove the offending '(', I get```
donn@donn-desktop:~$ aptitude search ?name apt
E: Regex compilation error: Invalid preceding regular expression
```So, my behavior is just like yours, and different from the behavior that the aptitude users manual predicts. This seems to be some kind of bug. Probably, aptitude is using another program (a parser) that is not happy with the Ubuntu system.

I think you should [submit a bug report]("https://launchpad.net/ubuntu/+bugs"). I searched briefly and could not find this bug reported yet. It is not a critical bug, but should be reported anyway.

---

### Post by doru001 on 2009-08-18
> **dstew said:**
>  I think you should [submit a bug report]("https://launchpad.net/ubuntu/+bugs"). I searched briefly and could not find this bug reported yet. It is not a critical bug, but should be reported anyway.
Done: 
[https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/415386](https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/415386)

---

### Post by kbdcalls on 2009-11-28
This ist a Problem from bash

```
aptitude search '?name(apt)'
```

is working

with best regards from Dortmund (Germany/NRW)

---

### Post by doru001 on 2010-01-16
> **kbdcalls said:**
> This ist a Problem from bash

```
aptitude search '?name(apt)'
```is working

with best regards from Dortmund (Germany/NRW)

It is not from the quotas: 

```
$ aptitude search '?name(apt)'
E: Regex compilation error: Invalid preceding regular expression
```But maybe we can find out what is the difference between our installations.

---

### Post by doru001 on 2010-01-20
```
aptitude search "?name(apt)"
```works well in  Ubuntu 9.10 Karmic Koala Desktop edition but not in Ubuntu 8.04.3 Hardy Heron Server edition.

---

