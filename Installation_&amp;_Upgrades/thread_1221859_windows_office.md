---
title: "windows office"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by jayanramesh on 2009-07-24
Dear pals,
How to install windows office 2007 in ubuntu using wine?

---

### Post by lukjad on 2009-07-24
[http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-9-04/](http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-9-04/)

---

### Post by moody_mark on 2009-07-24
Can I ask why you would need MS Office over Open office which comes as default in Ubuntu? Im just curious thats all, perhaps you need to write VBA apps?

---

### Post by lukjad on 2009-07-24
@  moody_mark   

I have noticed that when using Open Office for a Powerpoint presentation, the conversion does not work as well as it could since the timing is handled differently between the two programs. So the reason is probably for compatibility. 

@ jayanramesh

It occured that if you have a sufficiently powerful machine and a copy of Windows, you can also run Windows in Virtualbox.

---

### Post by jayanramesh on 2009-07-24
Dear lukjad007,
Thank very much.I installed wine 1.1.26 and windows office 2007 as directed .Everything went ok but office failed to start.please help me to solve this prob.

---

### Post by lukjad on 2009-07-25
Did you get any error messages?

---

### Post by jayanramesh on 2009-07-25
Dear lukjad007,
I don't get any error message just it refuses to start-why?
Thank you.

PS: My OS is jaunty 64 Bit-Is the "wine" ok with 64 bit?

---

### Post by madsmeg on 2009-07-25
to check for errors in wine, and yes wine works well with 64bit.

Open a terminal

type:

> wine path/to/office.exe

eg: > wine /home/madsmeg/Microsoft\ Office/Ofiice.exe

then list the last errors here, we may be able to help more then.

---

### Post by niceguy123 on 2009-07-25
I need to start working with a customers relation management system CRM that is based on Microsoft Access. What options do I have?  Would this work on wine or would I need dual boot?

Does running wine slow down the whole system?

Thanks,

---

### Post by madsmeg on 2009-07-25
wow... never thought people used access seriously

I have never had any performance issues with wine (on odd occasions applications run faster in wine than natively).

I will look into CRM with Access through wine now

---

### Post by madsmeg on 2009-07-25
What version of Access are your clients using, also, have you thought about using open office's version of database to manipulate the access database?

---

