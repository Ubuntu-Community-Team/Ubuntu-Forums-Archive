---
title: "Compaq Presario V6211 : Unable to install any Ubuntu"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by talkout on 2007-05-26
Dear all,

I got a new [Compaq Presario V6211 ]("http://h10010.www1.hp.com/wwpc/in/en/ho/WF06b/1090709-1116637-1123071-1123071-1123071-12925444-78223853.html")laptop which has
[LIST][*]AMD Turion 64X2 1.6GHz
[*]Video adapter NVIDIA® GeForce™ Go 6150
[*]Preloaded Vista Home Basic Version[/LIST]

I tried to install Ubuntu 7.04 64bit, 6.06 64bit, 6.06 32bit, Kubuntu 6.06 32bit

Bit I encountered the same following problems in all:
[LIST][*]It has got stuck while loading.Just after hardware check it hangs, doesn't proceed ahead.
[*]It is just throwing a blank screen.[/LIST]
I think this might be a problem due to my graphics card, but not sure. Because when I tried GParted Live CD, I had to go in after doing Forcevideo --> VESA --> 800x600

Can some one Please help...
Because I couldn't find any help from any other web online... 
I'm desperate to make my Vista Box into a Tux Box...

NiMaL-TalkOut

---

### Post by Ken_Lewis81 on 2007-05-27
I've always loaded the Ubuntu Desktop LiveCD's in safe graphics mode.  Since 6.06, the loader screen has had options for internationalization and display resolution, which is where I pick my keyboard settings and pick VESA or VGA graphics.

What happens when you do that?

Take care.
Ken.

---

### Post by talkout on 2007-05-27
There seems a solution in Ubuntu, but its not working completely.
When I boot in text mode with options **_live noapic nolapic acpi=off_** 
It boots in till Gnome login screen. But there it stops and nothing further.

Another guys who has the same laptop said me through an e-mail that he had the same problem.
And now he had installed ***Linux Mint*** with the same above options, and that worked.

So what could be the problem with Ubuntu?
I'm also gonna try Linux Mint. Downloading it now. Hope it works. 
In the mean time, if there is a solution for Ubuntu, please let me know. 
That will be helpful.
[INDENT]***Ken:***
*Thanks for your comment, I'll try what you said also.*
[/INDENT] Urs,
NiMaL

---

### Post by talkout on 2007-05-27
Finally after a two days of no sleep:sad: and Googleing and some lemon soda...
I'm writing this on Firefox on Feisty Fawn!

Yes guys, Finally I got the *Ubuntu 7.04 64bit Edition* Installed on my laptop.
This is what I had to do *(finally)*:[LIST=1]
[*]Press *ESC* to enter the text mode installation.
[*]Start the live CD with options *'live noapic'*
[*]Wait for a bit watching white texts...
[*]Wait for some more time watching the blinking '_'
[*]Wait for at least 5mins,* I had my dinner at that time* :wink:
[*]Gnome loads finally, *whoooh!*
[*]Start the install and proceed the normal way.[/LIST]For now it working fine for me. But not sure about other drivers...
Any now I'm on a Feisty Fawn!

NiMaL
[www.talkout.tk]("http://www.talkout.tk/")

---

