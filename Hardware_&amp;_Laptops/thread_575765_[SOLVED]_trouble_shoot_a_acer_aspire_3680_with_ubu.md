---
title: "[SOLVED] trouble shoot a acer aspire 3680 with ubuntu feisty"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by k33bz on 2007-10-14
ok, i just got my wireless working on my acer. So now i want to tackle the other minor things that bother me about this laptop.

1st:    To fix sound. Currently sound is not working, works with headphones, not on laptop itself.

2nd:   To have the wireless toggle light switch to come on when the radio is on and connected or searching for a network.

3rd:    To have the scroll button scroll and not pull up a right click menu.

Anyone that knows how to fix these problems, please respond.

Thanks

---

### Post by k33bz on 2007-10-15
ok, I now have sound enabled.  For anyone who has had problem with their Acer laptops not having sound, go to this thread. It works.
[HTML]http://ubuntuforums.org/showthread.php?t=532215&highlight=sound&page=2[/HTML]


However I still need help with the other things. Please do help if you have any knowledge on the rest.

2nd: To have the wireless toggle light switch to come on when the radio is on and connected or searching for a network.

3rd: To have the scroll button scroll and not pull up a right click menu.

---

### Post by PsycoGeek on 2007-10-15
Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=429182").  It solved my problems with the touch pad and sound.

My light works.  [Here]("http://ubuntuforums.org/showthread.php?t=551621") is how i fixed it (probably not going to help you much, though).

---

### Post by k33bz on 2007-10-16
> **PsycoGeek said:**
> Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=429182").  It solved my problems with the touch pad and sound.

My light works.  [Here]("http://ubuntuforums.org/showthread.php?t=551621") is how i fixed it (probably not going to help you much, though).


Thanks for the reply PsycoGeek, 

I took a look at both threads you linked. I already have sound working,  I just added the lines for the scoll pad,  Still dont work,  Will see if it works after I reboot.

As for the lights! I read that thread, and it seems to me the only way I would get it to work is to install a new card.  Let me know if that is correct.

Thanks again

---

### Post by k33bz on 2007-10-16
ok, the scroll key works now.

But if anyone has a way to fix the WIFI light please let me know.

---

### Post by PsycoGeek on 2007-10-16
> **k33bz said:**
> As for the lights! I read that thread, and it seems to me the only way I would get it to work is to install a new card.  Let me know if that is correct.

Thanks again

Well, for me it was an issue of the WiFi card not working at all.  If you are using an Atheros card it seems you might not have a light to indicate WiFi connectivity, from what I have been reading in different threads.  It may be due to using the NDIS wrapper, or it might just be that Ubuntu can't turn on the light with the Atheros card.  If you WiFi is working I would not worry about the light... it's just one less thing that will be drawing power when you are on the battery.

---

### Post by k33bz on 2007-10-16
well, all is fair.  Everything else is working.

so thanks alot PyscoGeek. your tips have helped out tremendously.

---

### Post by PsycoGeek on 2007-10-17
You are welcome.

---

