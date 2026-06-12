---
title: "grep: Support for the -P option is not compiled into this --disable-perl-regexp binar"
date: 2008-07-30
forum: General Help
---

### Post by keenlearner on 2008-07-30
How can I get the -P option to work in grep program ? 

>  -P, --perl-regexp
Interpret  PATTERN  as  a Perl regular expression.  This is highly experimental and grep -P may warn of unimplemented features.

I got error when trying to use it, clearly it's not implemented
> grep: Support for the -P option is not compiled into this --disable-perl-regexp binary


Thank you,

---

### Post by pauper on 2008-07-30
```
sudo apt-get install pcregrep
```

"Perl-style regexps have many useful features that the standard POSIX ones
don't; this is basically the same as grep but with the different
regexp syntax."

---

### Post by keenlearner on 2008-07-30
After 
sudo apt-get install pcregrep

grep: Support for the -P option is not compiled into this --disable-perl-regexp binary

Do I have to recompile on grep  ?


I love perl regexp, because I am more familiar with it, besides that it's the most powerful regular expression that I have ever use so far. Thanks

---

### Post by pauper on 2008-07-30
No, it's a different package, see "man pcre".
Check out [this link](http://linux.byexamples.com/archives/345/pcregrep-grep-based-on-perl-compatible-regular-expressions) and [that one](http://www.pcre.org/).

---

