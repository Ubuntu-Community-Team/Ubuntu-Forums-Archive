---
title: "OS Issues"
date: 2012-04-28
forum: Hardware
---

### Post by Axxon95 on 2012-04-28
I'm having an issue, with almost all Linux Distros(but having most luck with Ubuntu. 10.04, and 12.04).

I currently have Ubuntu 10.04 installed on a 40GB HDD I use to fool around with Linux(*no dual-booting involved*), it works perfectly with no issues what-so-ever.
I recently tried 12.04 and actually got it to boot into Live(*11.10 would loop when it found my USB devices, Mouse and Keyboard*)... but I have no X or anything, I just see the "_" blinking on the top left corner. Reason I know it's booting into live is that I hear the DVD drive spinning fast as usual, and then after a few minutes(*usually when it's done loading*) it spins down.
Additionally, I also fooled around by pressing Alt-TAB, and Tab a few times and pressing Enter to see if it actually is, and I can hear the DVD drive spinning fast again.
I don't know if its an issue with my new hardware or not, but I believe it is.

*Asus P8H61-M LE/CSM*
*i5 2500*
[I]4GBx2 Crucial Ballistics 1333MHz
EVGA GTX 460[/I]

Thanks, I hope this gets resolved. :/

---

### Post by Rodney9 on 2012-04-28
Check your CD/DVD

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Burn your CD/DVD at the slowest speed.

Rodney

---

### Post by Axxon95 on 2012-04-28
> **Rodney9 said:**
> Check your CD/DVD

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Burn your CD/DVD at the slowest speed.

Rodney

Thank you for your reply.
After I try a LiveUSB(to save a CD) first, then try burning another CD.

---

### Post by sir_cheats_a_lot on 2012-04-29
yeah, it does sound as if the cd wasn't "closed"(the lead out process) properly. There is such a thing as burning at too low of a speed as well; some drives won't even boot up a disc burned at lower then 8x, sometimes they will, but they'll only be read at a very low speed(personal experience, thought it was a glitch, until I burned another on another computer at similar speed).  the "LiveUSB" method avoids such things, and typically performs a little better.  let us know how it goes(there shouldn't be a problem).

---

### Post by Axxon95 on 2012-04-29
> **sir_cheats_a_lot said:**
> yeah, it does sound as if the cd wasn't "closed"(the lead out process) properly. There is such a thing as burning at too low of a speed as well; some drives won't even boot up a disc burned at lower then 8x, sometimes they will, but they'll only be read at a very low speed(personal experience, thought it was a glitch, until I burned another on another computer at similar speed).  the "LiveUSB" method avoids such things, and typically performs a little better.  let us know how it goes(there shouldn't be a problem).

I made a LiveUSB and still nothing. Boots up and only the blinking "_" on the top left.
I tried Linux Mint 12(which I think is a variant of Ubuntu) and sorta the same issue, I get looped on modprobe, as well as when it finds my Mouse and Keyboard(USB).
(signal 9)
Is it an Asus desktop motherboard issue?

Edit: The only Linux OSes I can get installed is Ubuntu 10.04, and Mandriva.

---

### Post by sir_cheats_a_lot on 2012-04-30
I see you've posted about this in multiple places, in any case, I'm almost tempted to say it's a ram issue.  if it was a board issue itself I don't think it'd even run 10.04 or mandriva, not unless there was a major kernel change between those and the latest versions.  And yes, Mint 12 is based on Ubuntu 11.10.  I think Ubuntu 10.04 will be supported until next April however.  There's no need to rush any software upgrades just yet.  If it works, use it.  In either case though, I'd suggest running memtest(it's a boot option on the CD), then find something to do for the rest of the day(it takes a while).  better safe then sorry. 

**Edit**

by the way, did you try the alternate install images yet? if not that maybe a route to investigate if you really want to use the latest version.

---

### Post by Axxon95 on 2012-04-30
> **sir_cheats_a_lot said:**
> I see you've posted about this in multiple places, in any case, I'm almost tempted to say it's a ram issue.  if it was a board issue itself I don't think it'd even run 10.04 or mandriva, not unless there was a major kernel change between those and the latest versions.  And yes, Mint 12 is based on Ubuntu 11.10.  I think Ubuntu 10.04 will be supported until next April however.  There's no need to rush any software upgrades just yet.  If it works, use it.  In either case though, I'd suggest running memtest(it's a boot option on the CD), then find something to do for the rest of the day(it takes a while).  better safe then sorry. 

**Edit**

by the way, did you try the alternate install images yet? if not that maybe a route to investigate if you really want to use the latest version.

I'll try multiple alternate ISOs, the only hard part is finding the time to do it(I'm always on my computer, nothing else to do.)

Edit: I don't know if this will help any, but all of the Linux OSes I threw at VirtualBox worked perfectly on my computer.

---

### Post by sir_cheats_a_lot on 2012-04-30
it's a long shot, but may also be a bios setting. *shrugs*  it is strange that it's running fine presumably on the same machine, under virtual box though.  if it's not a bios setting, which again is doubtful(you never know though), then maybe the alternate isos will work fine.  guess we'll have to wait and see, unless someone else has any better suggestions.

---

### Post by Axxon95 on 2012-05-02
I believe it stems from a BIOS setting, I turned off my external video card and I'm getting everything now.

Is there any workarounds?

---

### Post by Axxon95 on 2012-05-02
I have succeeded!

I switched my BIOS settings to iGPU, booted up Ubuntu, added Ubuntu-X PPA, installed NVIDIA drivers, and set the BIOS settings back to PEG/iGPU.

Thanks for the help.

---

### Post by sir_cheats_a_lot on 2012-05-03
ah, good to hear, don't forget to mark the thread as solved.

---

