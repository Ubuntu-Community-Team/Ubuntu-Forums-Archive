---
title: "getting/ using ndiswrapper &quot;stuff&quot; offline"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by uc50_ic4more on 2005-06-06
Hello -

I need to install Ubuntu on a laptop. This laptop, sadly, ticks me off in two ways:

1) The ethernet jack has (at least) some type of cold solder joint or something - it simply does not function, and all of my troubleshooting leads me to believe that the issue is tactile, so downloading anything from anywhere via the hard wired ethernet port is not viable.

2) The wireless card is a D-Link DWL-G630, which has no native Linux driver. I would like to be able to get and use all of the dependencies and such that I'd need to get the card working. Here has been my experience, and understanding, thus far:
     - Using the live CD, I have selected for install the "ndiswrapper", but a few KB need to be downloaded. Ugh. Let's remember - I have no functioing network connection.  ](*,)
     - There is mention in the description for "ndiswrapper" entry in the Synaptic Package Manager of the need to compile the source for some additional dependencies (specifically, the kernel module)... Is there a pre-compiled version? The thought of having to install gcc to compile anything is a potential tick-off #3...

Thank you!

---

### Post by Gtaylor on 2005-06-06
Check out: 
[http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.1-4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.1-4_i386.deb)

Other related files are available at:
[http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)

You can do a 
```

wget http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.1-4_i386.deb

```
Then transfer the .deb over to your other computer via CD/floppy. Then install it:
```

sudo dpkg -i ndiswrapper-utils_1.1-4_i386.deb

```
To install. Then you'll need your windows driver for the card (A .INF file). I'd recommend looking at the ndiswrapper webpage for a complete listing of supported cards and the driver they work with.

---

### Post by az on 2005-06-06
ndiswrapper is precompiled and on the install cd!

Just install ndiswrapper-utils (form the cd) and you are good to go...

---

### Post by uc50_ic4more on 2005-06-06
[QUOTE=azz]ndiswrapper is precompiled and on the install cd!

Just install ndiswrapper-utils (form the cd) and you are good to go...[/QUOTE]

azz - Hmmmm... That was my first inclination, but during the install process I was informed that 24KB (!) needed to be downloaded. I do not recall which file was the offending party.

Gtaylor - I will grab that .deb and see how she flies... Thank you both!

---

### Post by az on 2005-06-06
You do not need to be online to install.  Warty checks to see if you are and then tries to update the packages.  Hoary stopped doing that for the reason you describe.

You install from the cd and then get online and update afterwards.  Everything you need is already there.

---

### Post by uc50_ic4more on 2005-06-07
[QUOTE=azz]You do not need to be online to install.  Warty checks to see if you are and then tries to update the packages.  Hoary stopped doing that for the reason you describe.

You install from the cd and then get online and update afterwards.  Everything you need is already there.[/QUOTE]

azz - Let me re-iterate that I am using the *Live CD*. At this point I can only assume that this is the reason I am prompted to download, rather than the requisite files being present on the CD.......?

I am in the delicate process of gently cajolling my wife into allowing me to switch her laptop from Windows to Ubuntu, and I'd like a functioning Live CD demo for her before I proceed in earnest. The hard ethernet port not functioning is throwing a major wrench into the works.

Gtalyor - I transferred the .deb to my USB drive and tried to "-i" from there. After about 20 minutes (?!) of hearing the CD-ROM whirring around and watching my terminal doing not-a-heck-of-a-lot, I was still left with an error. This was over 12 hours ago now, and it was a little irresponsible of me to have *not* taken note of the exact verbage of the error message(s), but I will attempt it again today and report back precisely what was reported as having gone wrong.

Thank you both again!

---

### Post by Gtaylor on 2005-06-07
[QUOTE=uc50_ic4more]azz - Let me re-iterate that I am using the *Live CD*. At this point I can only assume that this is the reason I am prompted to download, rather than the requisite files being present on the CD.......?

I am in the delicate process of gently cajolling my wife into allowing me to switch her laptop from Windows to Ubuntu, and I'd like a functioning Live CD demo for her before I proceed in earnest. The hard ethernet port not functioning is throwing a major wrench into the works.

Gtalyor - I transferred the .deb to my USB drive and tried to "-i" from there. After about 20 minutes (?!) of hearing the CD-ROM whirring around and watching my terminal doing not-a-heck-of-a-lot, I was still left with an error. This was over 12 hours ago now, and it was a little irresponsible of me to have *not* taken note of the exact verbage of the error message(s), but I will attempt it again today and report back precisely what was reported as having gone wrong.

Thank you both again![/QUOTE]
Oh shoot, i didn't know you were on a Live CD, I've only briefly played with that thing and I'm not sure what to do in that case. Sorry :(

---

### Post by uc50_ic4more on 2005-06-07
[QUOTE=Gtaylor]Oh shoot, i didn't know you were on a Live CD, I've only briefly played with that thing and I'm not sure what to do in that case. Sorry :([/QUOTE]

No problem... At this point, I think I may have wrapped my head around the ndiswrapper install + the wpa-supplicant that I may just step bravely into a full install. If the full install works, I will report back to confirm that the Live CD in fact does *not* contain the files necessary to install the ndiswrapper.

---

### Post by Gtaylor on 2005-06-07
The full install should be very safe and there are a lot more people who can help with that :)

---

### Post by az on 2005-06-07
Right.  Livecd=no ndiswrapper.

Did not realise you were still talking about the live cd...

---

