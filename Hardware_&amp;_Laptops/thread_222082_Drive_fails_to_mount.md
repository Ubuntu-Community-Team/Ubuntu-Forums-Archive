---
title: "Drive fails to mount"
date: 2006-07-24
forum: Hardware &amp; Laptops
---

### Post by sojakfa on 2006-07-24
I have two hard drives in my machine. One is a 40gig drive formatted to NTFS that runs Windows XP. The other is a 120gig drive that just got reformatted and I installed this fine operating system on it.

The [Partitions and Booting]("https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html") section of the faqs says Windows partitions should automatically be accessible, but my XP drive isn't. I followed the instructions for making it accessible using the Disks Manager. I go to click Enable, all the buttons grey out for a split second, and then the window goes back to active and it's still inaccessible.

Any ideas?

---

### Post by loserboy on 2006-07-24
I had the same thing happen to me on a fat32 part i made for sharing... it's fixed now but I forgot how i did it

Edit: it has something to do with the mount location i'm checking into it some more

ok there we go...did you give it an access path?

---

### Post by sojakfa on 2006-07-24
No. I've no clue what that even means.

I'm a total linux noob. Used windows all my life, trying to get away >.<

---

### Post by sojakfa on 2006-07-24
I found a how to and got it working. Thanks :)

Edit: Well, crap. Got it mounted, it's reading that it's being used, but when I try to open it I get this:
```
The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "disks-conf-hda1".
```

For reference, [this]("http://ubuntuguide.org/wiki/Dapper#Windows") is the guide I used.

Anybody have any ideas what I need to do now?

---

### Post by damien.yep on 2006-07-24
hi!

Is it possible to open it with super user right? (sudo)
For exemple, if you want to display a text file, type:
$sudo cat myfile.txt

If you can see the content of your file, then I think its a user right problem. Is your drive accessible for every user?
If this is not working, then it's an other problem, and I may not be able to help you :( 

Good luck
Damien.

---

### Post by sojakfa on 2006-07-25
Got home from work, booted up, immediately came here to see if anyone replied. Minimized Firefox to try what you said and noticed a new hard drive icon on my desktop that magically lets me into my drive. Not sure how it happened, but I'm not going to complain!

Thanks for your help though!

Hmm... all my hardware works. Now just to make Guild Wars work and I can leave Windoze behind me forever!

---

### Post by loserboy on 2006-07-25
wine or cadega can prolly do that for you

---

### Post by wpshooter on 2006-07-25
> **sojakfa said:**
> Got home from work, booted up, immediately came here to see if anyone replied. Minimized Firefox to try what you said and noticed a new hard drive icon on my desktop that magically lets me into my drive. Not sure how it happened, but I'm not going to complain!

Thanks for your help though!

Hmm... all my hardware works. Now just to make Guild Wars work and I can leave Windoze behind me forever!

How it happened is that you probably made the correct change to get it working but you needed to reboot in order for it to take effect, isn't it nice of them to NOT tell you this !!!

---

### Post by sojakfa on 2006-07-30
The fix from that link seems to be working for me, but it stops working after reboot.

Any ideas?

---

