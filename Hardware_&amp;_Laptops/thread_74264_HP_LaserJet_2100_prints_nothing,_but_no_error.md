---
title: "HP LaserJet 2100 prints nothing, but no error"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by linhgb on 2005-10-11
I just did a server upgrade at this small office. The system is dual core A64 3800+ X2, NF4 SLI Ultra, 2GB RAM etc. I put Ubuntu 5.04 on it, with a compiled 2.6.13 kernel for A64 smp. It's basically a vanilla compilation and I kept most of the settings at default. This is an upgrade from the old server (dual P3) which had various Mandrake distros, and the printer, HP LaserJet 2100 (a legacy one which is supported widely I believe) has always worked fine with it.

Now back to the new server. It's working very well for me and Debian apt-get / synaptic is fantastic (I work with almost exclusively Debian based servers and workstations - now running Ubuntu). However, I just cannot get that damn printer to print something! Setup was straightforward. The printer was plugged in from the start. It was detected straight away off the LPT0 port, and was installed automatically. CUPS and all that jazz are installed. I hit print test page (or any page I care to try), printer LED lits up, sounds like it's doing something. Job goes into the queue, then disappears. Cups logs (even at more informative levels) say everything is kosher, job completed successfully. The problem is that nothing comes out! If the thing just gave me an error, I'd at least have a clue where to start. :( 

I've reinstalled the printer many times. I tried all available drivers (PPD ones) but it still fails on me. I've searched the forums and tried every trick I've found but nothing works. I know that the printer works because firstly it was working on the old (retired) Mandrake server and secondly it works with my windows laptop. I'm seriously considering putting the Mandrake server back on as a print server to stop the biatching coming from the clients, but I'd like to ask if you guys and gals have any advice for me. Very much appreciated!

---

### Post by mlomker on 2005-10-11
> I'm seriously considering putting the Mandrake server back on as a print server to stop the biatching coming from the clients, but I'd like to ask if you guys and gals have any advice for me. Very much appreciated!

Hmm.  Have you tried anything from the command line?

```

cat whateverfile.txt | lpr
lpstat

```

How about going into the BIOS and trying another LPT mode?  Not all printers like bidirectional.

I'd probably try booting up a Knoppix disc and printing as a test.

---

### Post by wylfing on 2005-10-11
I am not too sure about the BIOS being at fault, because the printer works with other OS. It is possible that something was misdetected at install time. Perhaps you should try going into the Printers control panel, deleting the printer, and installing it "manually" with Add Printer.

I can't tell from your post if that's something you've tried or not.

Edit: Er, after a more careful reading it looks like you *haven't* run any other OS on this particular hardware. So yes, a check in the BIOS would be a good way to go.

---

### Post by linhgb on 2005-10-11
I've done manual printer setup as well as trying to print from CLI. The BIOS trick is the one I haven't thought of. I vaguely remember having bidirectional on... I'll give that a go, and test it with a Knoppix bootdisk and a Mandrake live CD that I have here. wylfing, I haven't installed any OS on this machine except Ubuntu 5.04. What I meant was that this printer works with two other OSes on two different machines other than this one. 

Thanks for the tips, guys! Will report back after I get around to testing it (Friday).

---

