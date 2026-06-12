---
title: "ubuntu studio 8.1  text only?"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by colint1 on 2009-03-07
i just installed ubuntu studio right, but i didnt install it from a live cd, 

(i didnt go into a live cd version of ubuntu studio then clicked install ,like other ubuntu versions before)

but now im surprised to see when i turn my computer on it says the regular stuff then it asks me to login, all in text then password then it just gives me the same interface im used to seeing in a ubuntu terminal or something.

so the real question is: is ubuntu studio text only? (seem stupid)
and if not, any advice on how to fix?

---

### Post by fminmexico on 2009-03-07
> **colint1 said:**
> i just installed ubuntu studio right, but i didnt install it from a live cd, 

(i didnt go into a live cd version of ubuntu studio then clicked install ,like other ubuntu versions before)

but now im surprised to see when i turn my computer on it says the regular stuff then it asks me to login, all in text then password then it just gives me the same interface im used to seeing in a ubuntu terminal or something.

so the real question is: is ubuntu studio text only? (seem stupid)
and if not, any advice on how to fix?

I just installed from alternet cd and have same problem,how do you switch to graphical log in when it loads in text.
  fminmexico

---

### Post by kestrel1 on 2009-03-07
To start the X server type the following after you login```
startx
```

---

### Post by fminmexico on 2009-03-07
> **kestrel1 said:**
> To start the X server type the following after you login```
startx
```

tried that got    bash command not found.
   fminmexico

---

### Post by kellemes on 2009-03-07
Do you have different options to choose from at boot?
Like a different kernel? If so, try the one down from the top.

---

### Post by kestrel1 on 2009-03-07
Not sure if this will do anything, probably not but you could try.
What do you get if you press CTRL, ALT & F7 at the same time?
This normally switches to the graphical screen if it is running.

---

### Post by fminmexico on 2009-03-07
> **kellemes said:**
> Do you have different options to choose from at boot?
Like a different kernel? If so, try the one down from the top.

I have 2 other options tried both same result.
        fminmexico.

---

### Post by jespdj on 2009-03-07
Note that it is Ubuntu **8.10**, not 8.1.

The version number indicates the year and month it was released: 8 = 2008, 10 = October. The next version of Ubuntu will be released in April this year and will therefore be numbered 9.04.

---

### Post by mdharp on 2009-03-17
Same problem here. No desktop !! Tried all options on this thread, & it did download some packages for xinit but still no response to startx command, & no change after Cntrl>Alt>F7.
This Ubuntu Studio is looking like a bad joke ! I've lost countless hours trying to get amd & i386, 8.04.1 versions going. Could have gone busking & bought a good PC for the same effort.:(

---

### Post by mdharp on 2009-03-18
Just got some further tips from another "attempting" UbStudio user -
"..that happened here with studio 904 i386, so I chose the recovery kernel 
in GRUB, booted to command line with networking, 
sudo apt-get update 
then
sudo apt-get install'ed a couple video packages, rebooted,  and it worked."

maybe 9.04 beta is a better option ?
[http://cdimage.ubuntu.com/ubuntustudio/releases/9.04/alpha-6/](http://cdimage.ubuntu.com/ubuntustudio/releases/9.04/alpha-6/)

Hope this helps. Let me know (private message) if it works for you.

---

### Post by daniel_gv93 on 2009-03-19
I have the same problem! please post here if anyone knows how to solve it... or how to uninstall it in the worst case :S

---

### Post by mdharp on 2009-03-19
Still nothing here. No "official" UbuntuStudio support, as far as I'm aware, yet. I've gone back to Hardy install, with no RT kernel, as I tried installing RT kernel on Hardy 8.04 & it lost the desktop _AGAIN_ *&%$#@!!!

I'm starting to think this whole Linux thing is "programmers only" territory, despite the well meant offers of help & advice on forums & elsewhere. If the programs being developed are for media production, then they hopefully should be useable by media producers with a bit of perseverance & patience while learning the ropes. But I'm into this for about 2 weeks of wasted time & effort, copious notes taken from forum threads with a (hopefully) careful & methodical application of what I've learnt, with still no solid response, & still no solid audio / media system running.

Good luck !!

---

### Post by fminmexico on 2009-03-26
> **mdharp said:**
> Same problem here. No desktop !! Tried all options on this thread, & it did download some packages for xinit but still no response to startx command, & no change after Cntrl>Alt>F7.
This Ubuntu Studio is looking like a bad joke ! I've lost countless hours trying to get amd & i386, 8.04.1 versions going. Could have gone busking & bought a good PC for the same effort.:(

When you install Studio there is a screen where you have to use the space bar to choose what to install,make sure that you have the desktop install marked with the space bar.
  fminmexico.

---

### Post by mdharp on 2009-03-26
Hi Fminmexico.
When installing, it gets to "select & install software" list, showing Audio apps, video apps, Studio desktop & I think another one or two I can't remember.
It says you can select either one, two etc or all apps listed, but there is no "Install All" option. So I check first box on list, then allow it to complete installation, then before rebooting, I use "Go Back" option to "Select & Install" & select the next in list, & repeat this process until all checked apps are installed. Then I allow it to reboot & (hopefully) run as new install of Ubuntu Studio. 
This has never worked. Tried numerous times.:confused:

---

### Post by fminmexico on 2009-03-27
> **mdharp said:**
> Hi Fminmexico.
When installing, it gets to "select & install software" list, showing Audio apps, video apps, Studio desktop & I think another one or two I can't remember.
It says you can select either one, two etc or all apps listed, but there is no "Install All" option. So I check first box on list, then allow it to complete installation, then before rebooting, I use "Go Back" option to "Select & Install" & select the next in list, & repeat this process until all checked apps are installed. Then I allow it to reboot & (hopefully) run as new install of Ubuntu Studio. 
This has never worked. Tried numerous times.:confused:

When you come to this window use the space bar to x the first,use the arrow down then space bar for second etc.etc.
   fminmexico.

---

