---
title: "php-cgi problems"
date: 2005-11-13
forum: General Help
---

### Post by bartoni on 2005-11-13
I want to use php for some shell scripting but I've got php set up as an apache module.   I Read somewhere that you can run both php cgi and module versions together with no problems...

so I tried apt-get php4-cgi but got the following errors :

php4-cgi: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed

Can anyone help??

---

### Post by tehwa on 2005-11-13
If you want to use php for shell scripting, you can use ```
sudo apt-get install php4-cli
```

---

### Post by bartoni on 2005-11-14
Hi,

I get the same error.

php4-cli: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed

Same with php5-cli.  What is libc6, can I replace it with 2.3.2.ds1-20ubuntu14?

-edit-  seems I have 2.3.2.ds1-20ubuntu14 installed (I think) and 'apt-get install libc6'  tells me I already have the latest version.

---

