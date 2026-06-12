---
title: "fresh Ubuntu install internet trouble"
date: 2008-10-31
forum: General Help
---

### Post by runslikeapenguin on 2008-10-31
ive used Linux before but i am not super savvy with it, and i just set up two hard drives with the GRUB so i can run Windows for games and Linux for everything else. but one problem is that when in booted up in Ubuntu it cant connect to the internet. ive never had this problem with Linux before, its always just connected right up. 

any advice? i would love to get off XP and get into Ubuntu but without the internet that's not going to happen.

---

### Post by runslikeapenguin on 2008-10-31
any one?

---

### Post by southerngrey on 2008-10-31
Gonna need some more information.. What sort of internet connection do you have, what version of Ubuntu are you running?  What sort of device are you using for your network connection etc....

---

### Post by runslikeapenguin on 2008-11-01
DSL, ethernet from the motherboard and version 5.04 :oops: i know its old but i was planning on updating it, but no internet.

---

### Post by southerngrey on 2008-11-01
1. Is your network card detected and working.  Run

sudo lspci

in terminal and see if you can see your ethernet card listed.  If that is up and running did your ISP provide you with any DNS settings to enter?

---

### Post by runslikeapenguin on 2008-11-01
ok, im not at my computer now but i will try that, but i just talked to my friend on the phone and he just installed the newest version of Ubuntu on his laptop and he said that he cannot connect to the router that we have in our room but he can connect to the wireless thats set up for the rest of the house. 

so if its the router in our room any ideas on why it would be blocking Ubuntu?

---

### Post by southerngrey on 2008-11-01
Is your router set to allow connections from all hosts?  If it's set up to only allow hosts it recognises it could be denying the new OS host names.  Seeing as your both running different versions of ubuntu it seems unlikely its a bug, more likely a settings issue.  Is the wireless on the same router as the wired connection?

---

### Post by chaoswings on 2008-11-01
Is your router security enabled? linux can only read TKIP encryption properly forget AES. Also make sure that the router allows for all types of cards (N,G etc cards)

---

### Post by runslikeapenguin on 2008-11-02
i figured it out, the router was security enabled and we just had to set it up to allow our MAC addresses, and even then the internet wouldent work for me and it turns out it was just the old version of Ubuntu. it wouldent recognize my network adapter. so i got a newer version and it worked fine, i now have 8.04 now.

thanks for your help

---

