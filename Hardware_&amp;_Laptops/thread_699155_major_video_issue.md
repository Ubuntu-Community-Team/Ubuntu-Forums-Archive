---
title: "major video issue"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by djrunslinux on 2008-02-17
I sure hope someone can help me with this.I have a ibm think pad a21m.800 mhz 32o ram.I was running ubuntu just fine.Now after i login it will display a tiled ibm logo at the top of the screen tiled and then disappears.then then lower half of the screen is black until i hover over it with my mouse.I get it to go awaym then i open up Firefox and do a search and all the text is layers on top of each other.Once again if i hover over it with my mouse it will be display normally.But it seems to be an ongoing issue.My guess would be that the video memory has gone bad.What do you think? the video memory is attached to the motherboard,so i would have to replace that.I found one on ebay for 45 bucks.But would like to be more confident with what it is before i spent money.What do you think it is? does it sound like bad video memory to you? please let me know what you think.Thank you in advance.

---

### Post by SixedUp on 2008-02-17
Thinkpads (especially of that generation) had astonishing build quality ... they really were as close to bullet proof as you could get.  As such, I'd tend to look for software issues first. 

You didn't say how you'd debbugged this problem; does it show the same issues in the BIOS, or when running (say) Windows? Have you run the BIOS self-test routines? Finally, have you tried a reinstall of Linux? If it was me I'd want to be absolutely sure the problem is hardware-related, and not a software issue with my OS install before I started trying to desolder/resolder surface-mounted RAM chips ... have you seen how small those pins are, and how close together they are?

You might want to think about just getting a replacement motherboard (they're still available from specialists) rather than attempting to resolder components. It will be more expensive than your RAM chip, but you'll stand much more chance of getting it working again. 

Finally, the hardware maintenance manual (what the IBM service engineers used to fix these) is available here: [ftp://ftp.software.ibm.com/pc/pccbbs/mobiles_pdf/23p0896.pdf](ftp://ftp.software.ibm.com/pc/pccbbs/mobiles_pdf/23p0896.pdf). Good luck

---

### Post by Yellow Pasque on 2008-02-17
So it repeats this exact same behavior every time you boot? No, that does not sound like bad video memory to me, it sounds like a video driver issue. Please post your /etc/X11/xorg.conf file and the output of this command:
```
sudo lshw -C video
```

---

### Post by djrunslinux on 2008-02-17
I have reinstalled ubuntu breezy and the latest version multiple times.Also have attempted to install windows as well. and has thesame prob.On the windows install graphics go so wacky that I cannot even see what it is doing on the install.I even ran the damn small linux live cd and had the same problem.So do you think a new motherboard will fix this?

---

