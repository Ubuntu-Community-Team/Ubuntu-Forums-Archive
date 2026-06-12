---
title: "Ubuntu (live cd) doesn't run on my new laptop"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by ARXD on 2009-03-22
[COLOR="Red"](Solved, see post # 9)[/COLOR]
Dear community   
I have a new laptop [(HP TouchSmart tx2-1020CA, click here for more info)]("http://www.bestbuy.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0926INGFS10118242&catid=20354") that came with Vista pre-installed.

I am new to linux world and would like to install Linux Ubuntu on my new laptop. (it's time for me to move on to a real operating system)

I have downloaded the Ubuntu Live cd V8.10 and restart the laptop.
to be safe, I first chose "run Ubuntu with no changes to your pc"  and the laptop got stuck on this window:
[http://img21.imageshack.us/img21/3616/ubuntu.jpg](http://img21.imageshack.us/img21/3616/ubuntu.jpg)
then I tried again, this time with "ACPI-OFF" and I got this black screen:
[http://img19.imageshack.us/img19/7291/ubuntu2.jpg](http://img19.imageshack.us/img19/7291/ubuntu2.jpg)
That leads to nowhere...

Does anyone have an idea what's wrong? 
(I tried to install Ubuntu to my hard drive but I am getting the same scenario)

Please, Help me. ](*,)

---

### Post by lisati on 2009-03-22
One of the first things some people do is check that the CD is OK - most Ubuntu installation disks come with a "Check CD for errors" option. Another possibility is to see if the CD works in another machine.

---

### Post by linuxrollup on 2009-03-22
At the second screen, does it do anything?

---

### Post by linuxrollup on 2009-03-22
> **lisati said:**
> One of the first things some people do is check that the CD is OK - most Ubuntu installation disks come with a "Check CD for errors" option.

The "Check for CD defects" option takes ages though unless you have a fast CD drive.

---

### Post by lisati on 2009-03-22
> **linuxrollup said:**
> The "Check for CD defects" option takes ages though unless you have a fast CD drive.

Good point. :) It was just a thought. Sometimes it's easy to take what you have for granted and forget that other people's gear might have different capabilities.

---

### Post by ARXD on 2009-03-22
I check the CD as everyone suggested, (took a long time...) no errors.
also The Live CD work's fine on my Home PC.

*linuxrollup ask: At the second screen, does it do anything? *
- The laptop get stuck on the second screen and not doing anything

Any more ideas?
can it be that my brand new laptop is too new and can't run linux!?
:sad:

---

### Post by Favux on 2009-03-22
Hi ARXD,

I saw your other post.  I think HP calls them "TX2z" and that's probably what you should be searching with.  Or maybe HP has changed the naming nomenclature or more likely Best Buy has.  Check the plate on the bottom of the laptop.

See this thread, especially post #10 to install:

[http://ubuntuforums.org/showthread.php?t=1081529&highlight=tx2z]("http://ubuntuforums.org/showthread.php?t=1081529&highlight=tx2z")

Then go on to:

[http://ubuntuforums.org/showthread.php?t=1038898&highlight=Tablet]("http://ubuntuforums.org/showthread.php?t=1038898&highlight=Tablet")

Read the thread through before doing anything.  Glurgle asks you to do some stuff like removing the 10-wacom.fdi which I'm not sure is necessary.

Hope this helps!

---

### Post by spandon on 2009-03-23
Hi ARXD,

Disk problem can be discounted if it loads up Ubuntu on another machine.

I get the same result as you are getting on one of my computers, but it will work when I do the following:-

after selecting language and the main menu appears, press F6 and type
**noapic nolapic vga=771**   then press enter
Hope this works for you?
Don

---

### Post by ARXD on 2009-03-23
Hi

In the end I manage to install Ubuntu using the **V8.04 live cd**.
From some reason I had no problem running the V8.04 live cd on the laptop.
now Ubuntu is up and running and all I have to do now is to find the right drivers for the laptop... (WiFi, ATI and etc)

Thank you everyone for the support. ;)
Wish me luck....

---

