---
title: "Z35F - How I wish I could get sound to work."
date: 2008-10-13
forum: Hardware
---

### Post by Heather42 on 2008-10-13
Hi.
I have reinstalled from 7.10 to 8.04 on my Asus Z35F laptop. Having blind faith that the newer version would be more compatible, I found that I still have no sound and continue to have frequent freeze ups. I see there are very few Z35F people out there using Ubuntu. Is this laptop even worth the effort? Mr.Dave has a post on how to get the sound to work. I have tried it several times with no luck. Any help would be appreciated! 

H.O.

---

### Post by fearful on 2008-10-13
Double click the sound icon on your panel and in the settings choose ALSA mixer as primary output.

---

### Post by amituttam82@gmail.com on 2008-10-13
Hey there, 

To be honest with you I think you should try Suse or maybe even (god forbid) Debian. If you want something like Ubuntu then try Mandriva which used to have excellent hardware support for laptops some years ago. I know its a pain but hey you already upgraded to 8.04...so...Well that's my two cents....

Thanks for reading
Amit

---

### Post by Heather42 on 2008-10-13
Hi Fearful..
I have Alsa as my primary output, but still nothing.. Thanks anyway!

---

### Post by Heather42 on 2008-10-13
Hi Amit.

Thanks for your input.

I really like Suse. I had it installed on my Z35F and no sound like Ubuntu. Same with Mandriva. 

Any idea what might cause a window to freeze and turn grey? Can I monitor what is going on to see exactly what is taking place. 

I'd like to take this laptop back to the company that sold it to me as a Linux laptop but I've had it for over a year.

---

### Post by Heather42 on 2010-08-17
Its been 2 years since i posted this question. I still cant get sound with version 10.04.  Has Ubuntu forgotten us Z35F owners?

---

### Post by lidex on 2010-08-17
> **Heather42 said:**
> Its been 2 years since i posted this question. I still cant get sound with version 10.04.  Has Ubuntu forgotten us Z35F owners?

Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

