---
title: "Will not display/flashing blue sqaures"
date: 2012-03-13
forum: Hardware
---

### Post by Vynesh on 2012-03-13
Thank you for taking a minute to read this! 
 
I've been having multitudes of issues with my installing experience and now I've got it down to this!
 
After selecting Ubuntu from my boot list (installed via Wubi), my system takes a minute to display startup scripts (I think that's what they are). After waiting for these to finish.. BAM! black screen with random blue squares randomly flashing all over my screen. :confused: There are no faint images of anything in the background, no sounds, no error messages. My display just stops working right. A very helpful guy on my previous thread with my booting issues told me that it could possibly be that my chipset is not compatible. I'm not sure if this is correct, or how to fix it! :confused: As you can tell I'm completely new to using Linux, and have limited knowledge of coding/hardware. I've been troubleshooting this for two days now, any help would mean the world to me! 
 
My specs are:
 
Compaq Presario SR1503WM
Intel Celeron D 2.93GHz
1.5G RAM
70G HDD
Windows XP Home

---

### Post by Vynesh on 2012-03-13
Bump for Ubuntu~
Never used it, near giving up :( 
 
Please, any help would be awesome

---

### Post by Vynesh on 2012-03-14
Can someone please help me? :/

---

### Post by Mark Phelps on 2012-03-14
Hey ... I know this must be frustrating, but we're all volunteers here and repeated bumping will NOT get you any faster response.

The display problem is likely to be either a display hardware problem or video drivers problem or both.

If you're getting a proper display in WinXP, that rules out display hardware problems, leaving video driver problems.

You need to boot using an Ubuntu desktop CD, choose Try Ubuntu, open a terminal, enter "lspci" -- and look for the line containing "VGA".  That will list out the make and model of your video chipset.

Post that information back here -- and we might be able to help.

---

### Post by Vynesh on 2012-03-14
> **Mark Phelps said:**
> Hey ... I know this must be frustrating, but we're all volunteers here and repeated bumping will NOT get you any faster response.
 
I'm sorry, I really don't mean to seem pushy or actively trying to frustrate others. I haven't really used a forum to this extent before and I wasn't sure if posts just get 'lost in the lists' without bumping. I do appreciate the clarification!
 
> The display problem is likely to be either a display hardware problem or video drivers problem or both. 
 
I know it's impolite to open up two threads on the same subject, should I remove one? If so should I keep this under Hardware, or Install?
 
> If you're getting a proper display in WinXP, that rules out display hardware problems, leaving video driver problems.
 
You need to boot using an Ubuntu desktop CD, choose Try Ubuntu, open a terminal, enter "lspci" -- and look for the line containing "VGA". That will list out the make and model of your video chipset.
 
I tried using the CD's but I'm still getting the same thing. I went through my Device Manager in Windows and got **Intel 845GV** 
 
Thank you for your help again Mark!

---

### Post by 2F4U on 2012-03-14
If you haven't already tried, I would suggest that you try to boot with the nomodeset kernel parameter

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by Vynesh on 2012-03-14
> **2F4U said:**
> If you haven't already tried, I would suggest that you try to boot with the nomodeset kernel parameter
 
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
 
I haven't tried this yet! How do I go about doing this? I have minimal knowledge of coding and I have no idea where to look for/enter this stuff :-k

---

