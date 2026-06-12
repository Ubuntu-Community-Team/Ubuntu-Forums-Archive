---
title: "New USB thumb drive is read only, cannot save anything to it."
date: 2018-09-28
forum: Hardware
---

### Post by Euanbuntu on 2018-09-28
Hi there,

So, as per the title I'm having problems. I've tried using both GParted and Disks (Disk Utility) to reformat the new USB thumb drive but no joy. I then scoured the forums for similar issues, but I got a bit lost so I need to resort to asking if a kind soul might please help me to gain control over this pesky new USB drive.

Thanks in advance.

---

### Post by hrsetrdr on 2018-09-29
I gotta ask: does your userid have permission to access a USB?  

[Allowing-your-linux-userid-permission-to-use-your-usb-device]("https://github.com/GoldenCheetah/GoldenCheetah/wiki/Allowing-your-linux-userid-permission-to-use-your-usb-device")

---

### Post by sudodus on 2018-09-29
Maybe the following links (and links from them) can help you

[How to change ownership and permissions of automatically mounted HDD](https://askubuntu.com/questions/1043163/how-to-change-ownership-and-permissions-of-automatically-mounted-hdd/1043300#1043300)

[Mount NTFS partition in a USB drive with custom permissions and owner](https://askubuntu.com/questions/11840/how-do-i-use-chmod-on-an-ntfs-or-fat32-partition/956072#956072)

---

### Post by Euanbuntu on 2018-09-29
> **sudodus said:**
> Maybe the following links (and links from them) can help you

[How to change ownership and permissions of automatically mounted HDD](https://askubuntu.com/questions/1043163/how-to-change-ownership-and-permissions-of-automatically-mounted-hdd/1043300#1043300)

[Mount NTFS partition in a USB drive with custom permissions and owner](https://askubuntu.com/questions/11840/how-do-i-use-chmod-on-an-ntfs-or-fat32-partition/956072#956072)

Yes. I can access many other USB devices/thumb drives etc.

---

### Post by sudodus on 2018-09-29
So there are problems with one particular USB pendrive. Then maybe the following link can help you *analyze* the problem and if you are lucky, *solve* the problem.

[Can't format my usb drive. I have already tried with mkdosfs and gparted](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

---

### Post by Euanbuntu on 2018-09-29
> **sudodus said:**
> Maybe the following links (and links from them) can help you

[How to change ownership and permissions of automatically mounted HDD](https://askubuntu.com/questions/1043163/how-to-change-ownership-and-permissions-of-automatically-mounted-hdd/1043300#1043300)

[Mount NTFS partition in a USB drive with custom permissions and owner](https://askubuntu.com/questions/11840/how-do-i-use-chmod-on-an-ntfs-or-fat32-partition/956072#956072)


Thank you for these, but I am afraid I get completely lost after a few minutes trying to follow both of these methods. Could you please talk me through it.

Would it help if I posted some details of the USB? If so what commands should I use?

---

### Post by Euanbuntu on 2018-09-29
> **sudodus said:**
> So there are problems with one particular USB pendrive. Then maybe the following link can help you *analyze* the problem and if you are lucky, *solve* the problem.

[Can't format my usb drive. I have already tried with mkdosfs and gparted](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)


Thank you sudodus. I have already tried all of these with no joy. Maybe it's a brick :-/

---

### Post by sudodus on 2018-09-29
> **Euanbuntu said:**
> Thank you sudodus. I have already tried all of these with no joy. Maybe it's a brick :-/

If none of these methods works, yes, I'm afraid that your USB pendrive is damaged beyond repair.

---

### Post by C.S.Cameron on 2018-09-30
Thumb drives are getting higher and higher capacity at the expense of reliability.
I bricked a Kingston in just a couple days, did not even have time to try running Ubuntu from it.
So far I have had good luck with Sandisk and Lexar. 
My Lexar 128 has been working for over two years with a Full install on it.

---

### Post by Euanbuntu on 2018-09-30
> **C.S.Cameron said:**
> Thumb drives are getting higher and higher capacity at the expense of reliability.
I bricked a Kingston in just a couple days, did not even have time to try running Ubuntu from it.
So far I have had good luck with Sandisk and Lexar. 
My Lexar 128 has been working for over two years with a Full install on it.


This is good advice - thank you C.S.Cameron. Yes, the Kingston 128 I have is now a brick (as mentioned), but it never worked to start with. Off to Lexar I go! ;-)

---

### Post by Autodave on 2018-09-30
Dumb question: I have seen a few that actually have a switch that can be turned on or off.  Did you look for one?

---

