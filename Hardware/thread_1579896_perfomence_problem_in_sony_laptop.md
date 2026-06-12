---
title: "perfomence problem in sony laptop"
date: 2010-09-22
forum: Hardware
---

### Post by gudurukarthik on 2010-09-22
hi , im running ubuntu on a sony fw series 6 gb ram laptop. my question  is , i think ubuntu is not using my total ram , and i got this after i  had seen the system monitor and it shows   ''memory :2.9gb''. 
can any one help me in solving this problem . and please tell me if any  thing else i should be doing to improve my laptop performance .
thank you

---

### Post by Tylerjd on 2010-09-22
What version of Ubuntu are you using... x86 (32bit) or x86_64 (64bit)? 32bit processors are limited to 4 gbs of memory, but I don't know why it would only report 3 gigs. Make sure the RAM is seated properly as well.

---

### Post by gudurukarthik on 2010-09-22
hey thank u for the replay 
im a dam new to ubuntu in the first place . im using ubuntu 10.04(lucid) and i really dont know where to check and tell u whether im x86 (32bit) or x86_64 (64bit) , im really sorry for futting u in trouble but can u please help me out like where should check for it ... i think there is no problem with the ram as i used to use windows 7 and it used all my ram perfectly

---

### Post by e79 on 2010-09-22
> **gudurukarthik said:**
> hey thank u for the replay 
im a dam new to ubuntu in the first place . im using ubuntu 10.04(lucid) and i really dont know where to check and tell u whether im x86 (32bit) or x86_64 (64bit) , im really sorry for futting u in trouble but can u please help me out like where should check for it ... i think there is no problem with the ram as i used to use windows 7 and it used all my ram perfectly
 
Type in a terminal :
```
uname -a
```
 
The output can look somehting like this :
```
Linux ubuntu 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 **_i686_** GNU/Linux
```
 
The part that would interest you is the one in bold, stating which architecture you have :
 
i386/i686/x86 for 32 bit
x86_x64 for 64 bit
 
Hope this helps

---

### Post by gudurukarthik on 2010-09-22
out put was 
laptop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux
k so i understand that i have got a 32 bit ... 
so what sould i be doing to get my latop in to 64 bit

---

### Post by e79 on 2010-09-22
> **gudurukarthik said:**
> out put was 
laptop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux
k so i understand that i have got a 32 bit ... 
so what sould i be doing to get my latop in to 64 bit
 
The laptop is either 32 OR 64 bit, it cannot switch from one to the other, this is hardware related. A 32 bit operating system can be installed on a 64 bit computer but not the opposite. You would have to check at the specification of your laptop (your CPU for example would be a good start point).
 
The simpliest thing to do would be to download and burn an .ISO of the 'Ubuntu Desktop 10.04.1 amd64' (which is the 64bit version of Ubuntu) and fire your laptop with it. If you can boot all the way to the desktop, you can be pretty sure your laptop supports 64bits architecture.

---

