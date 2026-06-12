---
title: "mailx install without exim - how?"
date: 2008-07-14
forum: General Help
---

### Post by lenchen on 2008-07-14
Hi,

I'd like to install the package mailx. aptitude also wants to install several other packages, esp. exim, in order to resolve dependencies.

As I have already build my own qmail installation from source I don't want exim to be installed.

(1) How can I bring aptitude to install mailx without installing exim?

(2) Is it possible to perform (1) in a way that ensures that aptitude doesn't bother me with not-satisfied-dependency-messages when using it in future? Can I tell the package management system that it doesn't have to worry about dependencies in this case because qmail does exim's job?

Thanks for your help,

Lena

---

