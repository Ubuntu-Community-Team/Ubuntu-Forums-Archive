---
title: "computer can't boot any OS"
date: 2008-11-30
forum: General Help
---

### Post by li10 on 2008-11-30
The old comp I have in my room will  not boot windows 98 from the hard drive, Xubuntu or Puppy linux from the CD drive. Xubuntu and Puppy have kernel panics (xubuntu: "Kernel Panic - not syncing: attempted to kill the idle task!" along with other text) at which point they do nothing and you have to turn it off. Windows 98 does not start from the hard disk but I forgot what the error message was. I'll take a look.

Any help would be appreciated.

EDIT: windows says this:

"invalid VxD dynamic link call to device number 3, service B.
Your windows configuration is invalid. Run the windows setup program again to correct this problem."

I know VxD = drivers, but it doesn't make much sense otherwise except I've messed something up. I plugged in some new RAM (which is compatible( recently and unplugged an ATA from the motherboard to get to the RAM sockets. I plugged it back in but errr.

---

### Post by oilchangeguy on 2008-11-30
> **li10 said:**
> The old comp I have in my room will  not boot windows 98 from the hard drive, Xubuntu or Puppy linux from the CD drive. Xubuntu and Puppy have kernel panics (xubuntu: "Kernel Panic - not syncing: attempted to kill the idle task!" along with other text) at which point they do nothing and you have to turn it off. Windows 98 does not start from the hard disk but I forgot what the error message was. I'll take a look.

Any help would be appreciated.

have you thought about retiring that old computer? do you have the system restore cd? if so just reinstall 98.

---

### Post by li10 on 2008-11-30
I don't want to retire it because I don't have the cash, etc, and for experience (or something). 

The thing is the live discs don't work either which leads me to believe I've done something silly with the hardware, although the motherboard and BIOS detect the hardrive and CD drive. I'll just do what you say lol.

---

### Post by oilchangeguy on 2008-11-30
> **li10 said:**
> I don't want to retire it because I don't have the cash, etc, and for experience (or something). 

The thing is the live discs don't work either which leads me to believe I've done something silly with the hardware, although the motherboard and BIOS detect the hardrive and CD drive. I'll just do what you say lol.

let's try this again. do you have the restore cd(s) that came with the computer?

---

### Post by li10 on 2008-11-30
not that I know of/can find. I have the windows install cd though if that's any use.

---

### Post by brigadoon on 2008-11-30
> **li10 said:**
> I plugged in some new RAM (which is compatible( recently and unplugged an ATA from the motherboard to get to the RAM sockets. I plugged it back in but errr.

You have described two modifications to your system.

1) Plugged in some new RAM.
2) Unplugged an ATA from the motherboard.

Undo both changes and return the hardware configuration to where it was when you could last boot the system.

If the system doesn't boot then you may have caused some static damage (electro-static) when you added the RAM.

If it does work unplug the ATA and try to boot.

Then try installing the RAM.

Let us know what happens. If the system boots after the ATA is removed by not when you install the RAM then the RAM may not be compatible. The other explanation may be that you have to update the motherboard bios or adjust the IRQ settings.

What kind of PC is it? Manufacturer, model, etc...

---

### Post by oilchangeguy on 2008-11-30
a quick google check of the op's win 98 error message shows it's ram related.

---

### Post by li10 on 2008-11-30
> **brigadoon said:**
> 
What kind of PC is it? Manufacturer, model, etc...

It's a HP Kayak XAs with a pentium 2 processor.

EDIT: I actually put in 2 RAM modules, 1 128mb running at PC100 and another at 256mb running at PC133. the original RAM in the machine was 64mb running at PC100.

I took out the 256mb module and it seems to work now. Xubuntu boots from live cd.

I thought the RAM would run at slower speeds, and the speed they run at is set by the first RAm module in the motherboard. Is this something to do with that or is it to do with electrostatic charge on the RAM?

---

### Post by oilchangeguy on 2008-11-30
> **li10 said:**
> It's a HP Kayak XAs with a pentium 2 processor.

how much ram, and hard drive size? and what is the speed of that p2 cpu?

---

### Post by li10 on 2008-11-30
the hard drive is about 8gb or somewhere around that size. The processor is 300MHz I think, but I'm not totally sure.

---

### Post by oilchangeguy on 2008-11-30
> **li10 said:**
> the hard drive is about 8gb or somewhere around that size. The processor is 300MHz I think, but I'm not totally sure.

and the amount of ram is?????????????????????

---

### Post by linux6994 on 2008-11-30
Easiest thing to do with ram that may be problematic is to gently clean the edge connectors with an pencil eraser. Its easy and quick to do and in the past has help on various sorts of systems. Can't hurt to try.

---

### Post by TeXtonyx on 2008-11-30
It is as somebody said a ram error message.

Usually when the computer boots up, it flashes how much memory
the computer has. If not, you can find out in bios, by tapping
delete or some such key.

Do you know how much ram should have, after your adding to it?

In any event, the first thing to do is take out the memory that
you just installed and see if the computer boots. If it does
then the problem is specific to the new memory module rather
both or three of them, how ever many you have installed.

If the computer boots, the next thing to try is called "reseating"
the ram module. It's possible that you didn't push down hard
enough to fully embed the ram into the slot. Or, you can try
rebooting immediately to see if the computer works with just the
old memory and to gather motherboard information (possibly ram).  

If that doesn't work the new ram could be bad. Or just as likely
the replacement ram is the wrong kind. Since this computer is
older, the ram that it uses will be an older style, and it has
to be the same kind as the ram that was in there working before.

It is hard to find any techs or customer reps that are experienced
enough to just look at your old ram, if you took it out of the
computer and brought it to them and they then know what is the 
right kind to sell you. By far the easier way is to look up in your 
motherboard manual the right kind of ram to buy to fit your system.
If you don't have that mobo manual laying around then download
it from your particular motherboard manufacturer. That info is 
also listed in the bios by entering the bios by tapping the right 
key, often it tells you what key to tap during the boot up process. 

Since you have to take out the new memory anyway, a good time
to look for the motherboard model# is when you boot up to test
your system with the previous stick of ram. It's possible to
get the information off the motherboard directly but that often
can turn into a pita. While your taking out the ram, make sure
your hard drive cable is firmly connected to the hard drive and
the ide port on the motherboard, plus the data cable fits snugly.
You may be able to find out what mainboard you have from your
computer manual if you still have it, and it too, may be online.

I put things in this order because I think that reseating the
ram is not likely to work, but worth trying before you bring the
ram back to the store and (try to)replace/exchange it. 

Hooking back up any unreconnected old drive, if you didn't do
that already, has a low priority in light of your error message.

---

### Post by brigadoon on 2008-11-30
Please look at the back or underside of the pc and locate the model number. The hp web site is very detailed. All of the information required for the pc shall be there.

From my experience the available RAM configurations are dependent upon the motherboard design/configuration. A RAM configuration that works on a Dell may not work with a HP. Allowable memory configurations shall be detailed in the HP documentation available through their web site. However, to help you any further I need to know the model number of the pc.

---

### Post by oilchangeguy on 2008-11-30
> **brigadoon said:**
> Please look at the back or underside of the pc and locate the model number. The hp web site is very detailed. All of the information required for the pc shall be there.

From my experience the available RAM configurations are dependent upon the motherboard design/configuration. A RAM configuration that works on a Dell may not work with a HP. Allowable memory configurations shall be detailed in the HP documentation available through their web site. However, to help you any further I need to know the model number of the pc.

the op just needs to remove the ram they added. and try with the original ram. the "new" ram is probably the wrong type to work in the computer. like pc 133 and only pc 100 will work. and yes 133 should be backward compatible. but who knows.

---

### Post by TeXtonyx on 2008-11-30
> **li10 said:**
> It's a HP Kayak XAs with a pentium 2 processor.

EDIT: I actually put in 2 RAM modules, 1 128mb running at PC100 and another at 256mb running at PC133. the original RAM in the machine was 64mb running at PC100.

I took out the 256mb module and it seems to work now. Xubuntu boots from live cd.

I thought the RAM would run at slower speeds, and the speed they run at is set by the first RAm module in the motherboard. Is this something to do with that or is it to do with electrostatic charge on the RAM?

[http://search.hp.com/gwuseng/query.html?submit.x=7&submit.y=4&qt=HP+Kayak+XA++user+manual&la=en&col=hpcom+ccen+ccenfor](http://search.hp.com/gwuseng/query.html?submit.x=7&submit.y=4&qt=HP+Kayak+XA++user+manual&la=en&col=hpcom+ccen+ccenfor)

I looked at the technical manual, there is also a User Guide.
The first screen shot I will attach concerns your memory. The
other screenshot concerns using F-2 to enter bios setup where you
can change the boot order to cdrom first, in case you haven't.
Unless you have a newer model than the one I've used, this table
applies to your system.    Main Memory for HP Kayak XA:

Three DIMM sockets using:
32 MB, 64 MB or 128 MB ECC SDRAM to a maximum of 384 MB, or
16 MB, 32 MB, or 64 MB non-ECC SDRAM to a maximum of 192 MB

What this says is that it won't recognize a 256mb memory module.
But you want to test it to be sure. So take out the 128mb ram
which will test the 256mb ram stick standalone. I don't think it
will work, also based on your report above, but it's worth trying.

Besides, 256mb + 128mb = 484mb which exceeds the 384mb cap.
I think only the 64mb and the 128mb = 192mb ram will work so it, 
ECC or non-ECC won't matter, although ECC is the most upgradeable.

One more PC100, 128mb ECC ram stick costs about $16 and lets
your system qualify for those OS which require 256mb ram minimum
though I'm sure some of those small Linux OS will work with 192.

---

### Post by li10 on 2008-11-30
thanks for all the help guys, I'm just going to leave the 256 ram module out of the machine simply because it won't work (thanks a lot TeXtonyx).

It runs puppy nicely now which is great! :guitar:

---

