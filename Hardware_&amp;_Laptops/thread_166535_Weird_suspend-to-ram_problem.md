---
title: "Weird suspend-to-ram problem"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by pdobrev on 2006-04-26
Hello!
I have a DELL Latitude D510 laptop (Intel i915 graphics card) and have never had suspend-to-ram working properly. Currently I'm running the latest Dapper but I had the same problem with Breezy.
When I push the sleep button, it goes to sleep. Then sometimes it would resume nicely, and sometimes it won't. When it doesn't resume, I can hear some hard disk and also CD-ROM activity (some kind of a warm-up) but that's all. The screen doesn't go on and it's not the only problem because I can't operate the system anyway - it's not respond to any of my actions. 
I've also noticed that if you sleep and resume it right afterwards, it resumes nicely all the time. However, if I leave it suspended for a longer time, then it's a matter of probability if it'll wake up or not. 

Which suprised me even more (and may also have connection with the issue) is that it would suspend even if ACPI_SLEEP=true is commented in /etc/default/acpi-support. 

I've tried adding acpi_sleep=s3_mode and acpi_sleep=s3_bios as well, however, then it never wakes up. I put it to sleep, then turn it back on, and I get the same behavior as when my laptop refused to wake up using the previous configuration (w/o the s3_ thing).

If anyone has any clue or idea, please share, I'll greatly appreciate that!

Best,
Petar.

---

### Post by groggyboy on 2006-04-27
sorry to get your hopes up, but i don't have a solution.  i have the same problem, and it seems that we are [not alone]("http://www.ubuntuforums.org/showthread.php?t=141362").

groggyboy

---

### Post by obiwan on 2006-04-27
My suspend-to-ram works fine for me right now. The only problem that I've noticed is that when I resume sound doesn't works. Just killing esd and restarting it makes the trick.

(I have an inspiron 5150)

---

### Post by groggyboy on 2006-04-28
I've filed a bug report on Launchpad, #41969.

---

### Post by Luke on 2006-05-04
well, i think if it suspends with that line commented out, it means that you have some sort of power manager running that is actually controlling the sleep (prob the gnome power manager if that's included by default in dapper. i'm currently using xubuntu so i don't have all of the gnome stuff). 

i have read of cases where people need to use 
acpi_sleep=s3_bios,s3_mode

it's worth a shot

---

### Post by pdobrev on 2006-05-04
I don't know about the s3_mode, s3_bios stuff, but right now I'm using the suspend2 suggestion, offered here 

[http://www.ubuntuforums.org/showthread.php?t=141362&page=2](http://www.ubuntuforums.org/showthread.php?t=141362&page=2)
 
and it works ok so far  (a day and 2-3 sleeps/resumes). If it proves to be stable during the following days I guess I'll just stick to that. Another plus is that this prompted to install 2.6.16 kernel which gives some more battery life :)

If I don't forget I'll post the state of things a week or so later.

---

### Post by pdobrev on 2006-05-04
Ooops, I failure already. 
However, this one occured in strange circumstances. First, I closed my lid, then opened it and the screen light didn't turn on. Then I suspended the computer and resumed it right away (this has happened to me on several ocassions in the past). To my surprise - resuming did turn the screen light (backlight) on but still, that was all - just a lighted blank screen. I couldn't control the computer as I wasn't able to suspend it again.

Weird!

At least there is hope.

---

### Post by jwoertz on 2006-06-04
Hello-I have the same problem with my D510. How do you get it to come back up (break the cycle)? I have nothing on my screen except the mouse pointer. I can do a few things with the keyboard but can't get the GUI back. Thanks-Jeff

---

