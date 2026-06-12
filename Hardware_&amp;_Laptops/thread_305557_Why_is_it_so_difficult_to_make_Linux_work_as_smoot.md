---
title: "Why is it so difficult to make Linux work as smoothly as Windows"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by xp_newbie on 2006-11-23
In this particular case I am referring to the Hibernate and/or Suspend function.

I recently managed to solve [an amazing ordeal trying to make Ubuntu Dapper run reasonably on my ASUS P4P800-E Deluxe based desktop]("http://ubuntuforums.org/showpost.php?p=1776697&postcount=16").

This is great, as it finally drove me to change the default boot entry in GRUB from Windows to Ubuntu. :)

However, some things that I absolutely got used to in Windows, do not seem to work in Ubuntu. One of them is power management:

In the "Power Management Preferences" I tried:
* "Put computer to seleep when it is inactive for 30 minutes" and
* "Sleep type when inactive" = Hibernate

(I didn't even try Suspend, since it pops up a warning message saying that  it is not reliable).

However, after the system goes to Hibernate mode, then attempt to wake it up, it wakes up but then does all kinds of funny things - that eventually result in a running CPU (plus moderate disk activity) - and a **blank screen**. :( 

If I delve into the problem and spend weeks of learning the innerworkings of this, I may be able to find a solution (just as happenned with the "confused interrupt" described in the link I provided above), but... does one really need to be a computer expert to use Linux? I thought that Ubuntu was conceived mainly to address this problem!? :confused: 

Also, if I spend weeks and months to solve various problems, isn't this defeating the purpose of computing? After all, I bought the computer so that it works for me - not vice versa.

Any ideas or thoughts about how to make Hibernate work without investing too much time on the problem?

Thanks!
Alex

---

### Post by ingo on 2006-11-25
try suspend, why not? it works out of the box on my tp 600e (which is unheard of!) and if it doesn't work all you have to do is reboot.

my 2 cents' worth...

---

### Post by xyz on 2006-11-25
> In this particular case I am referring to the Hibernate and/or Suspend function.
Check my sig...worked for me.
Good luck.

---

### Post by ReaderRat on 2006-11-25
> **Why is it so difficult to make Linux work as smoothly as Windows**

[**[color=RED]Linux Is Not Windoze[/color]**](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by xp_newbie on 2006-11-25
Thank you guys for replying so far, despite the provocative title. ;) 

"Linux is not Windoze" - that I know and that's exactly why I am trying to switch to Linux. However, that fact by itself does not address the fundamental problem of trying to attract as many people as possible to Linux as a desktop, not only as a server.

Now here is an interesting piece of information that may be able to help someone provide me with the right tip:

I actually have Ubuntu installed on another ASUS motherboard based system: It is **Ubuntu 6.10** on a **P4P800 Deluxe**. Hibernate there **works perfectly**. :D 

However, on my main workstation, **Ubuntu 6.06 **on a **P4P800-E Deluxe**, Hibernate does not work. :( 

Notice, the only difference is the "-E" ...

Or is it 6.10 vs. 6.06?

But I can't use 6.10 on my main workstation as I need the stable one for work purposes.

Any suggestion?

Thanks,
Alex

---

### Post by houstonbofh on 2006-11-25
Vendors test all there hardware with Windows.  They write and provide drivers for Windows.  Some of them choose to ignore Linux.  Until enough people avoid them, and go to Linux friendly vendors, this will continue.  Your observation that one board works perfect and another does not, is a typical example.

---

### Post by umanzor on 2006-11-25
What houston said is true. I don't know, I guess this goes to every distro, but you actually have to learn how to use. Like, how to install packages, how to get drivers, how to make things work. Basically, be ready to read, search, and ask. I've found these last weeks some seriously cool apps that totally kill some of my needs of rebooting into windows...

---

### Post by DJFreestyler on 2006-11-25
> **xp_newbie said:**
> "Linux is not Windoze" - that I know and that's exactly why I am trying to switch to Linux. However, that fact by itself does not address the fundamental problem of trying to attract as many people as possible to Linux as a desktop, not only as a server.
You seem to have missed one point of that entire article: Most linux users dont want to attract as many users as possible. They just want an OS that THEY can use to the full extent, they dont create an OS that is easy for traumatized windows users and get as many people as possible. I suggest you read it again, as its a great article. (And thanks for the link ReaderRat ;) )

---

### Post by wirelessman on 2006-11-25
I work for a phone company installing DSL and troubleshooting networks; my hands are on all kinds of computers......trust me, after the nightmare of trying to keep Window computers (a couple of dozens) running this year, Ubuntu has been and still is a breath of fresh air.  I have moved a number of computers over to Ubuntu. People (some are good looking) love me for this.

---

### Post by doobit on 2006-11-25
> **xp_newbie said:**
> 
Notice, the only difference is the "-E" ...

Or is it 6.10 vs. 6.06?

But I can't use 6.10 on my main workstation as I need the stable one for work purposes.

Any suggestion?

Thanks,
Alex

I think it's a good chance it's the 6.06 vs. the 6.10 or actually the kernel versions. Remember that 6.10 also has a much newer, patched, kernel which is likely to work with more recent hardware or, in your case, BIOSs that use different power management systems. Your issue is a power management issue. Manufacturers change stuff like that in the BIOS all the time, and when they ship the computer, they include the drivers for thier hardware already installed. Notice - THEY ship the drivers. They are not necessarily included in a base install of Windows. They do, however, cooperate with Microsoft, so the drivers are quickly available on the Microsoft update site - for Windows, not for Linux. The Linux drivers may be available if someone makes them. I recently sent a wireless card to a developer so he could make drivers for it because there was not a package available yet. He had them for me and shipped my card back in a couple of days. I then supported the developer's project with cash.
That's community development. If you have a problem with the Linux community, then the community expects you to do more than complain about your poor situation. Contribute to make the situation better.

---

### Post by xp_newbie on 2006-11-26
> **DJFreestyler said:**
> You seem to have missed one point of that entire article: Most linux users dont want to attract as many users as possible. They just want an OS that THEY can use to the full extent, they dont create an OS that is easy for traumatized windows users and get as many people as possible. I suggest you read it again, as its a great article. (And thanks for the link ReaderRat ;) )

You are right - I didn't notice that the sentence "Linux is not Windoze" was actually a link to an article. Thanks for pointing this out.

I just finished reading it and I am even more confused: Is the article in favor of Linux or against it? :confused: 

Thanks,
Alex

---

