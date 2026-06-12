---
title: "Ran out of input data"
date: 2005-12-15
forum: Installation &amp; Upgrades
---

### Post by qbxk on 2005-12-15
i've burned like 5 cds now, using various burning apps under both Windows and Ubuntu (Hoary) - but they all keep doing the same thing.  The first 2 cds were sourced from a torrent-downloaded iso (ubuntu-5.10-install-i386.iso) and the other 3 were from the ubuntu servers direct - though of course they both passed the md5, they're identical...

when booting, i get to the boot: prompt, enter something (just about anything valid) and it will print:

```

Uncompressing Linux...

     ran out of input data

-- System Halted

```

And some variation of that on just about every machine i try to boot it with.

I have only used a single cd burner for these, and come to think of it, a single brand of cds.  Are these my problems or could there be software to blame?

thanks for any suggestions

---

### Post by exkalibur on 2005-12-15
Ok....First : are you trying to install or run from a live cd ?

Second : Is your cdrom setup in the bios as a boot device ?

Third : What app are you using to burn the iso image ?

Regards

---

### Post by qbxk on 2005-12-16
> Ok....First : are you trying to install or run from a live cd ?

install.  ubuntu-5.10-install-i386.iso

> Second : Is your cdrom setup in the bios as a boot device ?
i'm past that.  i get the boot: prompt.  it waits, i look at the pretty faded letters.  i hit F4 to see what else i can try.  then i hit enter (or type "linux vga=777 noacpi" or some other permutation, i tried em all) and it starts doing things, too quick to write down, load this that and then on Uncompressing linux... ran out of input data.  everytime, every machine. - wait no, some cds have instead gone into a "reboot loop" where they hit that step, reboot, then boot: prompt, enter, reboot, etc...

> Third : What app are you using to burn the iso image ?

i've the kde one on Hoary, uh, K3B i think?
on windows (2000) i've used:
cdburnerXP
Nero Express v. 6.0.0.24
and CDRFE (cdr tools front end) - which incidentally i found mention of on another forum post, and is a very fine package.  simple and robust. ( [http://demosten.com/cdrfe/](http://demosten.com/cdrfe/) )

some several times.... and according to the cdrfe output my burner won't go slower than 4x - i think it's got to be the burner that's the problem... still listening for help though.  thanks

---

### Post by exkalibur on 2005-12-16
A google search doesn't return anything conclusive....Do you have access to a different computer ? If you try your cd's on another machine and the problem still exists then, the media is probably the culprit.
 
Is there an OS on that computer that you're trying to install to ? If so, Is it working OK ?
Give us a bit of info on that machine ( hardware, proc,etc..)
 
I don't know what the result could be but, is virus protection turned on in the bios ? If so, turn it off. And I would run memtest on that box, just to be certain....
 
I'm still looking......

---

