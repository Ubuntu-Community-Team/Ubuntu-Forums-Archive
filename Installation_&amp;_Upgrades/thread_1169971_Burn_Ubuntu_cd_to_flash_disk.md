---
title: "Burn Ubuntu cd to flash disk?"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by Camilia on 2009-05-25
Due to hardware problems unable to burn ubuntu onto CD on my mother's computer with os windows xp. 

Was wonder for next visit if I can burn ubuntu CD, which I have at home, onto a flash disk.

---

### Post by g00f on 2009-05-25
Boot off a live CD on your PC and go to System, Administration, USB Startup disk creator. Is that what you want?

If it's not there do "sudo apt-get install usb-creator".

---

### Post by Camilia on 2009-05-25
> **g00f said:**
> Boot off a live CD on your PC and go to System, Administration, USB Startup disk creator. Is that what you want?

If it's not there do "sudo apt-get install usb-creator".

Yes!! I shall try it when I get home.

---

### Post by hesapotman on 2009-05-26
There are a few ways to do it ... But you can skip the CD completely and just create your Ubuntu Live USB using an ISO image of Ubuntu and a Windows program called "Ubuntu Live USB Imager". It allows you to create a bootable USB directly from Windows.

[http://phatwares.dyndns.org:8080/contentUU.html]("http://phatwares.dyndns.org:8080/contentUU.html")

Good luck!

---

### Post by Camilia on 2009-05-26
> **hesapotman said:**
> you can skip the CD completely and just create your Ubuntu Live USB using an ISO image of Ubuntu and a Windows program called "Ubuntu Live USB Imager". [http://phatwares.dyndns.org:8080/contentUU.html]("http://phatwares.dyndns.org:8080/contentUU.html")

Good luck!

Very interesting!!\\:D/ I shall try it later! 

Will it be installed as a program and easily removed after finished using it? For have found that some programs impossible to remove and generate icons. Can't take a chance that would happen on mom's computer.

---

### Post by Camilia on 2009-05-26
[http://phatwares.dyndns.org:8080/contentUU.html](http://phatwares.dyndns.org:8080/contentUU.html)

Looking at this site more and more becoming waring of downloading it for it has a lot of nasty advertisements. Will google for another link for similar program.

---

### Post by Camilia on 2009-05-26
http://phatwares.dyndns.org:8080/contentUU.html[/url]

Looking at this site more and more becoming waring of downloading it for it has a lot of nasty advertisements. Will google for another link for similar program. 

I think I found one called uSbuntu Live Creator. It is supports Ubuntu 8.10, Kubuntu 8.10 and Xubuntu 8.10. Thus now have to download ubuntu 8.10.

---

### Post by sgosnell on 2009-05-27
Just boot from the live CD, choose to try Ubuntu without making any changes to the computer, then open System/Administration/USB Startup Disk Creator.  Nothing else is needed, nothing needs to be put on the HDD of the computer.

---

### Post by hesapotman on 2009-05-27
> **Camilia said:**
> Very interesting!!\\:D/ I shall try it later! 

Will it be installed as a program and easily removed after finished using it? For have found that some programs impossible to remove and generate icons. Can't take a chance that would happen on mom's computer.

No installer - just a standalone application.

---

### Post by hesapotman on 2009-05-27
> **Camilia said:**
> [http://phatwares.dyndns.org:8080/contentUU.html](http://phatwares.dyndns.org:8080/contentUU.html)

Looking at this site more and more becoming waring of downloading it for it has a lot of nasty advertisements. Will google for another link for similar program.

Well ... sorry you don't like the ads. But that's how the site makes money. Ubuntu might be free, but servers are not.

The application is 100% free and contains no such ads. Also, it does Kubuntu and Xubuntu just like the other app you mentioned.

---

### Post by hesapotman on 2009-05-27
> **sgosnell said:**
> Just boot from the live CD, choose to try Ubuntu without making any changes to the computer, then open System/Administration/USB Startup Disk Creator.  Nothing else is needed, nothing needs to be put on the HDD of the computer.

As the original poster said, "Due to hardware problems unable to burn ubuntu onto CD ..."

So that won't work. Otherwise, you're absolutely correct about how it would be done under normal circumstances.

---

### Post by Camilia on 2009-05-27
> **hesapotman said:**
> 
The application is 100% free and contains no such ads. Also, it does Kubuntu and Xubuntu just like the other app you mentioned.

Thanks for the headup. I shall try it! For having problem getting ubuntu 8.10 downloaded

---

### Post by g00f on 2009-05-27
> **hesapotman said:**
> As the original poster said, "Due to hardware problems unable to burn ubuntu onto CD ..."

So that won't work. Otherwise, you're absolutely correct about how it would be done under normal circumstances.

It says on the left he's running Ubuntu (I assume on his PC, not his mothers), so if he does a "sudo apt-get install usb-creator" and has an .iso available he can do it that way without needing a CD/DVD drive at all.

---

### Post by Camilia on 2009-05-28
> **g00f said:**
> It says on the left he's running Ubuntu (I assume on his PC, not his mothers), so if he does a "sudo apt-get install usb-creator" and has an .iso available he can do it that way without needing a CD/DVD drive at all.

I don't comprehend this comment. I am in another state using my mother's computer that has windows xp os.  There is no terminal to paste a sudo command.

---

### Post by sgosnell on 2009-05-28
As you said in the original post, you can make a USB live disk at home, and install it during your next visit.  If you already have Ubuntu installed at home, it's quick and easy to make a live USB drive.  If you have access to a Ubuntu .iso at your mother's, you can use unetbootin to make a USB install disk.

---

### Post by Camilia on 2009-05-31
I don't have a usb or excess to store to buy one here thus just have to make one for next trip. Impossible to copy anything onto a CD either.

Thank you everyone.

---

