---
title: "sound card detection problem"
date: 2009-02-20
forum: Hardware
---

### Post by Arnab Dewanjee on 2009-02-20
hi everyone...i am a novice user of ubuntu...i've installed the ubuntu 8.10 version a couple of hours ago....the problem is that, the system cannot detect my sound card (creative live value 5.1)....it's detecting the built in card on the main board instead....could ne of u please help me out....thanx in advance....:-)

---

### Post by taurus on 2009-02-20
Go into the BIOS to turn off the onboard sound card or blacklist it in /etc/modprobe.d/blacklist.

---

### Post by Arnab Dewanjee on 2009-02-20
thanx mr taurus...as i.ve said that im just a beginner,though i've opennned the file u reffered to...i don't get how to blacklist it...or what changes to be made in this very file....could u please help me with that?....

---

### Post by taurus on 2009-02-20
What kind of onboard sound card does it have?

```
lspci
```

---

### Post by Arnab Dewanjee on 2009-02-20
the name shown is ICH5/ICH5R...so i think what i hv to do is write 'black list ICH5' and then save the file and then restart.....doing that the system will detect my sound blaster card with its 5:1 support?

---

### Post by taurus on 2009-02-20
Here is my onboard sound card

```

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

```
and these are the lines that I have in /etc/modprobe.d/blacklist

```

# sound drivers
blacklist snd-pcsp
blacklist snd_via82xx

```
so it would use my Creative Labs SB Audigy PCI card.

Therefore, adding **blacklist ICH5** to /etc/modprobe.d/blacklist is probably not going to work.

---

### Post by Arnab Dewanjee on 2009-02-20
i have inserted the lines 'blacklist snd_pcsp'...and 'blacklist snd_ICH5' for my on board card..'intel ICH5'....it now detects my sound blaster audio card...but still doesn't wrok.....i dont get the sound output....:(

---

### Post by Arnab Dewanjee on 2009-02-20
actually...eventhough the showing card is the saound blaster one....i am still getting output from the on board card.....:(

---

### Post by Arnab Dewanjee on 2009-02-20
hey mr taurus...one more ques....how do u configure the rear pannels of ur sound system...cause the 'rear depth'option doesnt manage well to configure them.....thanx a lot for ur help....

---

### Post by taurus on 2009-02-20
Go into System -> Preferences -> Sound and see which _D_evice: your system is using.

---

