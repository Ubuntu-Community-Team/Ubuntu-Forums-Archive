---
title: "Helping someone get graphics drivers"
date: 2013-06-24
forum: Hardware
---

### Post by lemonoid on 2013-06-24
Okay so I've recruited a friend back to Ubuntu who stopped using it a while ago. He was having issues getting 13.04 working, graphics-wise. I had the same problem, I have an older PC so I just decided to stay on 12.04 because of this and I told him to get 12.04 going first and get everything working fine and then try 13.04 live. I told him to try live first anyways but he just went for an install, but replaced it with 12.04. Idk what's going on with his graphics but he asked me to help him determine his current graphics card and get the proper drivers. He sent me a screenshot and for some reason it showed (what looked like) two different AMD Radeon cards to me. I'm not a guru at reading output especially when idk what command he's running, so long story short I'm here trying to find the easiest way to just get a line of single output (or a single graphics card result) if possible about what graphics card he's running and how to install his drivers. thanks for the help. I've been around google a bit with this, but I just always find my best help here.

---

### Post by carl4926 on 2013-06-24
It sounds like it might be hybrid graphics
It can be troublesome.
Some people can disable one in the BIOS
Some people(nvidia users) can use Bumblebee
Some people Blacklist one permanently

---

### Post by scbingham on 2013-06-24
Acting as a go between will be a real pain, especially when you can't see what commands are being typed or the output. Why not get your friend to log onto the forum & ask the questions directly?

There are many knowledgeable people on here & they will ask specific questions & need to see the results.

---

### Post by Mark Phelps on 2013-06-24
Ran across a similar situation on this forum and the person not only had two AMD graphics chips, they had two different versions -- and the problem was that one version would NOT work with AMD restricted drivers, while the other would.  In that case, the solution was to stay with the default Radeon drivers.

In the case of Hybrid or Switchable graphics, the PCs come preloaded with Windows and with special drivers that work in that mode.  AMD does not supply hybrid drivers, so if you force the installation of AMD drivers, unless you can disable one of the graphics chips, the drivers will not work.

This is not Windows, you don't just go charging around forcing the installation of new drivers.

---

### Post by gordintoronto on 2013-06-24
The command to find out what graphics adapters are present is: lspci

It should produce about 15 lines of output, including one (or two?) which look like this:
01:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9400 GT] (rev a1)

If the computer is a desktop, look at the back of it. If there are two VGA ports in different slots, there are two video cards.

---

### Post by lemonoid on 2013-06-24
> **Mark Phelps said:**
> Ran across a similar situation on this forum and the person not only had two AMD graphics chips, they had two different versions -- and the problem was that one version would NOT work with AMD restricted drivers, while the other would.  In that case, the solution was to stay with the default Radeon drivers.

In the case of Hybrid or Switchable graphics, the PCs come preloaded with Windows and with special drivers that work in that mode.  AMD does not supply hybrid drivers, so if you force the installation of AMD drivers, unless you can disable one of the graphics chips, the drivers will not work.

This is not Windows, you don't just go charging around forcing the installation of new drivers.

[IMG]http://i1269.photobucket.com/albums/jj596/DoseOfAndroid/aaronsAMD_zps7ccd3309.jpg?t=1372107447[/IMG]

This was the output I was referencing. Is this saying that there are two different Radeon HD graphics cards? When he went to System Settings and Details, under Graphics it said Vesa:rs880m, which sort of matches the first highlighted result above. 


referencing someone above who was talkin about bein a go-between, I can  communicate directly with him while he works, and he works all day and  night pretty much, if I can't figure it out for him then I will get him  to get on himself.

---

