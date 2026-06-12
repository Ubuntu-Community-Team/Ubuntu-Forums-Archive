---
title: "Acer Laptop Wireless problem"
date: 2011-05-22
forum: Hardware
---

### Post by JohnFDay on 2011-05-22
I installed Ubuntu 9.10 on my Aunt's ACER LAPTOP 5535.

Everything went well, and everything is working just fine....EXCEPT.........

The wireless will connect to the network, but it WILL NOT STAY connected.  It is constantly dropping the line and trying to re-link.  More often than not, I have to reboot before it can establish the link again, only to lose it (again) after just a minute or so.

Any idea what's happening here?  Is there, perhaps, an updated wireless driver that I can download and install?  I did check on the ACER website, but the only systems they "officially" support is Windows.

She was originally running Windows Vista and said this problem never happened, which DOES point to a software problem...at least, I think so.

Any help will be greatly appreciated.

Thanks in advance.
John F. Day

---

### Post by coffeecat on 2011-05-22
I've done a search for which wireless chipset you have in the Acer 5535, which didn't turn up anything definite, but I suspect you have the Atheros AR928X device. If so, the fix in 9.10 was to install a couple of backported modules packages. Except you can't do that now - Karmic/9.10 is no longer supported and you won't be able to install anything.

However, the good news - **if** you have an Atheros AR928X wireless device - is that wireless will work stably in Lucid/10.04, Maverick/10.10 and Natty/11.04. I have the Atheros AR928X in my Acer 7540 and that has been my experience.

So. Two things. Boot up Ubuntu and post the output of:

```
lspci
```So that we can be sure which wireless chipset you have.

Second thing is, whatever wireless chipset that laptop has, you need to install a later version of Ubuntu. I would suggest 10.04 since it's supported for another 18 months yet.

Out of interest, why do you install 9.10?

---

### Post by JohnFDay on 2011-05-23
To COFFEECAT:

THANKS for your input.  Ya know, I've been installing 10.04 for the last X months, but when I was driving up to Rhode Island, I just grabbed the wrong disk.  ERGO, 9.10 got installed.

I will be working my aunt through the upgrade as soon as she returns my call.

I am a very strong advocate of Ubuntu.  Beats the living hell out of ANY MS Windows.

I do believe this will solve the problem.

I will reply again with a follow-up once I know how the upgrade works.

Again, thanks much!

John Day

---

### Post by coffeecat on 2011-05-23
Good luck with that, but please check the output of lspci - post it if you can. If the wireless chipset is not the AR928X my earlier comments might not be relevant.

---

### Post by JohnFDay on 2011-05-26
Okay!  Finally received my Aunt's Acer through UPS.  (She's in RI, I'm in VA).

I checked the LSPCI and sure as heck...wireless chipset AR928X was there.

I upgraded the system to 10.04.1 LTS and everything is now working 100% perfectly.

(I've also thrown out my 9.10 CDs, to insure I don't install the wrong version again!)

Thanks for your input.  It is truly, deeply appreciated.

John F. Day

---

### Post by coffeecat on 2011-05-27
Excellent news. Good luck with 10.04.

---

