---
title: "Getting *.deb files from downloaded software through the repository."
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-04-07
1)Suppose I've installed...suppose WINE from the repository.

Is there anyway I can get .deb package from the contents downloaded?


2)Native Debian downloads of WINE say dependency failure...can I know what libraries etc...they need to get installed?

---

### Post by firefly2442 on 2009-04-07
So after you install a package, you are looking for the .deb file that got installed?  If so, look in /var/cache/apt/archives/

HTH. :)

---

### Post by Pasdar on 2009-04-07
> **firefly2442 said:**
> So after you install a package, you are looking for the .deb file that got installed?  If so, look in /var/cache/apt/archives/

HTH. :)

Woa, so many files I have there. Is there any issue with deleting them?

---

### Post by Therion on 2009-04-07
> **dE_logics said:**
> 1)Suppose I've installed...suppose WINE from the repository.

Is there anyway I can get .deb package from the contents downloaded?
I'm confused...  Do you want to CREATE a .deb file from the files you downloaded using Add/Remove or Synaptic for, using your example, WINE?  

Or do you want to FIND a .deb file for WINE?

---

### Post by dE_logics on 2009-04-07
Ok thanks for the location.

[quote=Therion]I'm confused... Do you want to CREATE a .deb file from the files you downloaded using Add/Remove or Synaptic for, using your example, WINE?

Or do you want to FIND a .deb file for WINE?[/quote]

I want to find them, but can you pls tell me how can I make them too?...I guess I need to have real understanding for that.

---

### Post by firefly2442 on 2009-04-10
> **Pasdar said:**
> Woa, so many files I have there. Is there any issue with deleting them?

No, it should be fine.  I would use this though:

```
sudo apt-get clean
```

This will clear the cache for you.

---

### Post by pbpersson on 2009-04-10
[Here is the online Intrepid page for Wine.]("http://packages.ubuntu.com/intrepid/wine")

You can download the .DEB file and you can also view the dependencies

---

### Post by lcs81 on 2009-04-10
I am new to Ubuntu. I am looking for cpp_4%3a4.2.3-1ubuntu6_amd64.deb. Where can i download this package? 

I notice that any package come with '%' cannot be download. what doest '%' mean? i do see some package come with '%'. 

Actually i am looking for cpp_4%3a4.2.3-1ubuntu6_i386.deb. I was given a set of 64bits packages to run a application.  I wanted this application to run on 32 bits system. Hence i am looking the same package but in 32 bits. 

;) Thanks

---

### Post by pbpersson on 2009-04-10
> **lcs81 said:**
> 

Actually i am looking for cpp_4%3a4.2.3-1ubuntu6_i386.deb. I was given a set of 64bits packages to run a application.  I wanted this application to run on 32 bits system. Hence i am looking the same package but in 32 bits.



If it is a 64-bit application, will it even run with 32-bit libraries?  If you were told it needed 64-bit libraries, attempting to substitute 32-bit libraries sounds like a bad idea.

Here are the version numbers of the packages:

HARDY-UPDATES:  4:4.2.3-1ubuntu6: amd64 i386 
INTREPID:  4:4.3.1-1ubuntu2: amd64 i386 

The cpp package is the The GNU C preprocessor.

Just install the CPP package for your version of Ubuntu and see if it works

---

### Post by lcs81 on 2009-04-12
Basically i was given a application that run on 64bits hardware with 64 bits Ubuntu installed. The script can also run on 32 bits system provided the same package installed on 32bits OS. I found most of the 32 bits' package but could not find those pacakage with the name has '%'. I found this package in 64 bits. Isnt that any package come in 64 bits should have 32 bits as well?

---

### Post by Slim Odds on 2009-04-12
> **dE_logics said:**
> 2)Native Debian downloads of WINE say dependency failure...can I know what libraries etc...they need to get installed?

Why would you want to do that?

You're just asking for trouble. Install Ubuntu stuff from the Ubuntu repositories.

---

