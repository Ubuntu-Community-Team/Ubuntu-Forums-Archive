---
title: "Citrix ICA Client"
date: 2008-09-17
forum: General Help
---

### Post by waapwoop1 on 2008-09-17
Hi People,

Has anyone got this working on their UBUNTU?

Thanks

---

### Post by cotcot on 2008-09-18
Not yet.
I am trying out [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?p=1997835#post1997835") howto but I do not succeed in downloading en.linuxx86.tar.gz from the citrix website. I think that the download folder is just empty. The japanese download works but I is of no use for me.

Was anybody able to download it recently ?

---

### Post by kaboodle_fish on 2008-09-18
> **waapwoop1 said:**
> Hi People,
 
Has anyone got this working on their UBUNTU?
 
Thanks
 
 
Yes

---

### Post by kaboodle_fish on 2008-09-18
> **cotcot said:**
> Not yet.
I am trying out [[COLOR=red]this[/COLOR]]("http://ubuntuforums.org/showthread.php?p=1997835#post1997835") howto but I do not succeed in downloading en.linuxx86.tar.gz from the citrix website. I think that the download folder is just empty. The japanese download works but I is of no use for me.
 
Was anybody able to download it recently ?
 
 
Try here 
 
[http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755&c2=ost1349860](http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755&c2=ost1349860)

---

### Post by cotcot on 2008-09-18
That is where I tried and failed.

---

### Post by cotcot on 2008-09-18
OK I have found another download area and could install the ICA client.
My last step is to install ssl certificates of which i only have an .exe file from my company.
Is there a way to convert it to something useful for ubuntu install ?

---

### Post by kaboodle_fish on 2008-09-18
Did you get it sorted?

---

### Post by cotcot on 2008-09-18
The ICA client works but the ssl certificates not.
Did you had to install ssl certificates ? If yes did you get a linux executable to install the certs ?

---

### Post by kaboodle_fish on 2008-09-18
I did not have to install the certs, no. 

It may be worth creating a new thread to see if anyone else can help

---

### Post by empty_spaces on 2008-09-18
Here is an older thread with the exact same name that I responded to. Follow the link in my post in that thread. Please use the search function next time.

[http://ubuntuforums.org/showthread.php?t=860578](http://ubuntuforums.org/showthread.php?t=860578)

---

### Post by waapwoop1 on 2008-09-18
OK guys,

I got mine working, here is what i did:-

I downloaded the tar.gz file. The install would not run :(

What i did was download the .rpm file, i used Alien to convert it to a .deb (never done that before) and it worked! great. 
So i installed the package.  then what?  I was a little confused.
I installed the motif package from apt-get. 
I found where ICAClient was installed, and i could open it from there. So from my company's site, it asked me where the program was to open the .asp file... i pointed it to the citrix client.  no certificates.
Was totally confused where to put the SSL certificates.
They were .cer files. 
In the ICA Client folder, there is a keystore folder. I renamed the .cer to the same extensions as in that folder, .crt or something. And the certs worked.
Everything worked. Can use Citrix now fine. Easy. sort of.

---

### Post by waapwoop1 on 2008-09-18
> **cotcot said:**
> The ICA client works but the ssl certificates not.
Did you had to install ssl certificates ? If yes did you get a linux executable to install the certs ?


you could install them on a windows PC. Export them from the certs section in windows.
they might be .cer, copy to linux desktop, rename to .crt and put int he keystore folder.

---

### Post by cotcot on 2008-09-19
I have seen the post you mention. It does not help me further with the ssl.

---

### Post by cotcot on 2008-09-20
> **waapwoop1 said:**
> you could install them on a windows PC. Export them from the certs section in windows.
they might be .cer, copy to linux desktop, rename to .crt and put int he keystore folder.
I have the cert installed on a windows pc. I exported it as PEM, DER, PKCS#7 and tried to import them in ff on ubuntu. The files are not recognised as certification files and there it stops. DER and PKCS are recognised as executable, PEM is recognised as text file. 
The filename as a .be extention (as for belgium). I renamed it to .crt and imported it. However it does not work.

---

### Post by ericesque on 2008-10-06
I installed the windows citrix client in Wine.  Worked like a charm! I fought with the native version for a long time - it never crossed my mind to try Wine :lolflag:

---

