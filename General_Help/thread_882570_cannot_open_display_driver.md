---
title: "cannot open display driver"
date: 2008-08-07
forum: General Help
---

### Post by KS1987 on 2008-08-07
I use Ubuntu 8.04 as a guest OS through Sun's VirtualBox with Windows Vista Business as host OS. I tried to alter the max resolution through adding the virtualbox additions and installing the .run driver found on the site of ati. Then I tried with the virtualbox manager. Why do I tell all of this, it's because I want you to bring to the same conclusion like I have. It's probally not about the virtualbox.

Furthemore, when I go face to face with my terminal. And I even dare to use a "gedit" command to touch my xorg, I get "cannot open display driver". I tried the faq about getting your gfx cards work properly. I tried misc. *solutions* posted about fixing this problem, none wanted to work. Even when I use the "sudo nautilus" command, I get "cannot open display driver". This is rather annoying, considering I have a 1280*800 resolution and a greyish area, whereas I wanted a 1680*1050 resolution. Any input is much appreciated.

---

### Post by kpkeerthi on 2008-08-07
Installing the ATi driver in a virtualized OS will not work as your host OS hides the ATi hardware from the virtual OS. Install the virtualbox guest additions for Vista (which I'm not sure how to do it in Windows) and reboot your guest Ubuntu. Now try to adjust the display settings of Ubuntu.

---

### Post by KS1987 on 2008-08-07
I don't mean to be offensive, but I did already do this. I've stated this in my initial post. I do know that hardware & misc. of a virtualized os comes from it's host, but I was at the end of my latin and I tried various ways to make it work. But all of this still doesn't explain the "cannot open display" error.

---

### Post by kpkeerthi on 2008-08-07
Can you try this?
1. Boot your guest Ubuntu in recovery mode (from the GRUB menu)
2. At the command prompt type
```
dpkg-reconfigure -phigh xserver-xorg
```
3. When prompted, choose the driver as 'vesa' and the appropriate resolutions you want
4. Type **reboot** at the command prompt
5. Boot into Ubuntu in normal mode.

Let me know if it made any difference.

---

### Post by KS1987 on 2008-08-07
Thank you, it did solve one thing. When I go to full screen of my virtual box, my Ubuntu takes up the full screen. However, when I typ in "nautilus", I still get "cannot open display". I did like you told me, but after typing the first command, I just got a message that I possible overwrite a custom file and that it back'up'ed to a certain file. I wasn't prompted for a driver or what-so-ever.

---

### Post by kpkeerthi on 2008-08-07
OK... can you post a screenshot of the exact message? Does nautilus open?

---

### Post by KS1987 on 2008-08-07
Nautilus doesn't open. I have to typ in nautilus --help for more info, that does work. But a command like nautilus --browser does not. 
```
root@USERpc:~# nautilus
cannot open display: 
Voer 'nautilus --help' uit voor een volledige lijst van opdrachtregelopties.
```
btw: the last line states that I should use nautilus help to see a full list of command line options.

---

### Post by kpkeerthi on 2008-08-07
OK... so it is "cannot open display" and NOT "cannot open display driver" as your title mentions. So the dpkg-reconfigure command makes no sense in this context as it has to do with display/driver configuration only.

---

### Post by KS1987 on 2008-08-07
I see now the error in my ways and I feel like quite the idiot. Any help regarding my general problem? I get the same output after typing "gedit". If that can help... Thank you.

---

### Post by KS1987 on 2008-08-08
> **KS1987 said:**
> I see now the error in my ways and I feel like quite the idiot. Any help regarding my general problem? I get the same output after typing "gedit". If that can help... Thank you.
using gksudo instead of sudo did the trick.

---

### Post by matey3 on 2008-09-11
Can someone help out here?

I am NOT running any Virtual stuff but I keep getting the message CANNOT OPEN DISPLAY:
I have tried gdm, kdm install xdm, Nautilus, xserver-xorg and another 120 megs worth of stuff to No Avail?

Do I have to run Windows XP to get graphics?
come on.. the older version 7.04 seemed a lot easier than this..I am not happy with 804 at all!

---

