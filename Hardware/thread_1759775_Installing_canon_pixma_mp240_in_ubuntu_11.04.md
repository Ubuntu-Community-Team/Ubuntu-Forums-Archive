---
title: "Installing canon pixma mp240 in ubuntu 11.04"
date: 2011-05-16
forum: Hardware
---

### Post by Robcubbon on 2011-05-16
Hi, I'm new to Ubuntu and having real trouble getting my printer to work. Its a canon mp240, I've had trouble finding the drivers and when i follow the instructions to extract and install them they don’t work and it crashes the software centre. I'd found a workaround last week and have already forgotten it. It did print a test page fine and still scans using simple scan, but no printing. The print app says the jobs been sent, the printer's indicating that its receiving but nothing comes out. It copies fine so I don’t think its a printer issue either.

Any help?

---

### Post by elchapu on 2011-05-30
Hi, try this [http://www.turboprint.info/](http://www.turboprint.info/)

---

### Post by pezunite on 2011-06-17
Hi GUys,

Im also new and dont even know where to start a new thread...

I have tried to install MP240 on 11.04
 but i could only get the scanner to work.. and when i go to print, the little screen on the printer lights up but nothing actually prints...

anyone can help me... please asap

---

### Post by LEP-Recon on 2011-08-16
Same problem here.  I can install the scanner just fine, just the printer that won't...

---

### Post by demonipuch on 2011-08-16
> **LEP-Recon said:**
> Same problem here.  I can install the scanner just fine, just the printer that won't...

Hello try these commands :

```
sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-mp240series
```

This will add this [ppa]("https://launchpad.net/%7Emichael-gruz/+archive/canon"), update your source list and install the drivers.

---

### Post by LEP-Recon on 2011-08-17
Worked like a charm, thanks!

---

