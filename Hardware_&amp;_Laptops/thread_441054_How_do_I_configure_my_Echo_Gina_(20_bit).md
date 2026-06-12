---
title: "How do I configure my Echo Gina (20 bit)?"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by Bartje on 2007-05-12
Hey all,

I've installed UbuntuStudio, and want to use my Echo Gina (20 bit version), so I've moved it from my 'windows-PC' to this 'Ubuntu-PC'. Now I want to reconfigure the audio system, which should be possible according to the hardware-list of ALSA. 

I ofcourse don't know how.

anyone familiar with configuring audio-cards?

Greets,

Bartje

---

### Post by Bartje on 2007-05-13
Really nobody that knows anything about Gina? Or configuring soundcards? 

Weird...

---

### Post by fiddler59 on 2007-05-13
I had no luck getting my layla3g to work with feisty final or ubuntustudio, There is a helper for the Mia card that tells you to build alsa from scratch (do a search for Mia under the ubuntu forums). I can't get alsa to compile under feisty....My solution was to go to 64 Studio.
It configured my layla3g on install. If audio production is what you want 64 Studio seems to have less setup hassles than any other audio distro plus an honest RT patched kenel to boot. 64 Studio is offered in 32 and 64 bit versions.

David B

---

### Post by Bartje on 2007-05-13
Ah, thanks fiddler.

I now use Ubuntustudio. I hope it will have less trouble than feisty. I'll take a look at 64 studio, but I pray it supports my 965G chipset and j-micron sata controller. Ubuntu is the only distro that can run on my computer so far, without having to search a patch to solve the above mentioned trouble. Without the support for the j-micron driver, the install CD or DVD even won't be read, no boot, no install... 

Weird, I see 64 studio also is based on Debian.. strange that there still is such a difference.

---

### Post by robb. on 2007-07-05
> **fiddler59 said:**
> ...there is a helper for the Mia card that tells you to build alsa from scratch (do a search for Mia under the ubuntu forums).

doesn't ALSA come with feisty?  when i ran synaptic, most of ALSA was already there.  would i have to re-compile it to make it work with my mia?

thanks for the tip on studio64.  i will look into that and report back.

thanks.

robb.

---

### Post by Bartje on 2007-07-05
ALSA does come with ubuntustudio, indeed, but after some searching there appears to be something wrong with the card itself, or with the pci-slots, because the card doesn't even get detected. I've tried 'lspci' to list the devices, but it doesn't find the card. I almost can't believe the pci slots are not working, because it's a brand new PC. The card itself worked fine on my previous computer. I still have to switch it back to that one to test the card. I had a tip to switch off the powermanagement in the bios, but I can't, because that option does seem to exist in the bio I have. I then tried different IRQ settings, but that gave no difference at all.
Even a fresh install, with the card in the computer did not give any effect.

---

### Post by robb. on 2007-07-05
this strikes me as odd, simply because my comptuer is a SFF with only one PCI slot.  feisty definitely recognizes that there is a card in the PCI slot, and it even identifies the motorola DSP chip on the card, but it clearly has no idea what to do with it past that.  it probably doesn't help that my motherboard has integrated audio, so that gets identified as "the" audio hardware automatically.

regardless, i will be looking into a few options.  i have heard there is a version of ubuntu studio that automatically recognizes the mia.  that may be my best bet.  there is also [this  guide at the alsa projet site](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Mia-midi.&chip=Motorola+56361&module=mia) that i am going to spend some time with.  if for no other reason than my own edification.

robb.

---

### Post by fredj on 2007-07-06
Alsa does support the echo gina but the ubuntu version of alsa may not include this support so you may have
to compile it yourself. Look on the alsa site and choose echo corporation as the manufacturer.

---

### Post by robb. on 2007-07-06
awesome.  thanks.

i knew the answer would be something simple like that.  we'll see how it goes this weekend.  with both getting regular ubuntu to use my mia and then seeing what happens with ubuntustudio.

robb.

---

### Post by robb. on 2007-07-07
ok, so i decided to get over my inexperience with command line.  i'm following the [wiki for the echo mia](https://help.ubuntu.com/community/EchoMia) by Curtis Brown.

i dowloaded the drivers from alsa-project.org (alsa-driver-1.0.14rc4) and unzipped them into /usr/src/alsa-driver-1.0.14rc4.  now when i try to run ./configure, i get the following message:

[quote=error in command line]checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.[/quote]

obviously it's not compiling.  here is the content of config.log:

[quote=config.log (snip)]
configure:2347: checking for C compiler default output file name
configure:2374: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2377: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
|
| int
| main ()
| {
|
|   ;
|   return 0;
| }
configure:2416: error: C compiler cannot create executables
See `config.log' for more details.[/quote]

what's happening?  should i create conftest.c?  what's the next step in making this work?

**thanks** for the help.

robb.

---

### Post by amias on 2007-11-05
It looks to me like you are trying to build in a directory that you do not have permission to write 
into .  chmod will help you here.

I am also trying to get a layla3g working with ubuntustudio , its very odd because the module
is loaded but jack won't see it because there are no relevant device nodes in /dev/snd .
This makes me think that rebuilding alsa won't help.

It looks to me as if there is no udev config for these cards .

Could whoever it was who switched to studio64 give us a copy of the relevant udev scripts/options ?

Toodle-pip
Amias

---

### Post by hogiewan on 2008-05-14
I'm sure the guys who posted on this thread fixed their problem, but to make sure others can find an answer, I'm adding this.  

You just need to compile and install the alsa firmware packages that match the alsa driver already installed.

at the command prompt type: 
```
cat /proc/asound/version
```

get the version of the firmware to match from alsa-project.org

make sure you have the "build-essential" package installed, then configure, make and (sudo) make install

---

