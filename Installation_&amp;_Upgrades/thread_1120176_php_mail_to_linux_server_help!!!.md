---
title: "php mail to linux server help!!!"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by lahp on 2009-04-08
hello basicly for months on and off i been trying to find an answer to my mail problem i cant get any mail sent from a form on the website to get sent from the server =[ what to do ? 

i have all the programs i need as im aware please some one help me maybe its the config or maybe i need a speical php code?

---

### Post by lahp on 2009-04-08
bump

---

### Post by nquinnathome1 on 2009-04-09
[LIST]
[*]What version of Ubuntu are you running?
[*]Are you using the Desktop or Server Edition?
[*]What mail applications do you have installed?
[/LIST]

We can't give you any help until you provide a little more info on your setup.

---

### Post by lahp on 2009-04-09
ubunru server 8 ...

sendmail, dovecot and some others but im willing to change any program =/ i dont mind and thts all i know its ubuntu server the one off the website large full 8.04 i think it is exact

---

### Post by lahp on 2009-04-09
BUMPPPPPYYYYYYY!!!:guitar:

---

### Post by nquinnathome1 on 2009-04-10
Sendmail has had a lot of security issues; I'm not sure how well-documented it's installation on Ubuntu is, and I know it can be pretty complex to configure.

Why don't you give Postfix a try instead? It's well documented so there shouldn't be any issue setting it up, and just like Sendmail, you can configure it to work with PHP's mail() function.

See here: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

