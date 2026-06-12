---
title: "Toshiba p100 Nvidia GPU overheating FIX (hardy heron)"
date: 2008-04-27
forum: Hardware
---

### Post by daimaru on 2008-04-27
[COLOR=Red][B]EDIT: I did not need to apply any patches anymore with Phoenix Bios 4.80, ubuntu 9.10 Kernel 2.6.31-17-generic, Nvidia driver v.185 It worked right out of the box. But only after a clean install. Before that I did a distupgrade from 9.04 to 9.10 and it did not work. With clean install as I said it works out of the box for me ( 57° right now )
[/B][/COLOR]

If the fix worked for you post your model name number. Thanks.
EDIT:  Works with: 8.10, 8.04, 7.10, 7.04

Well I guess everyone with a toshiba p100-something laptop that runs a nvidia graphics card was hoping that in hardy heron (ubuntu 8.04) the gpu overheating problem would have been solved. Though luck it hasn't! So you still have to do some work to get it running at a nice 40° instead of 100°. Read on.

Here's a short guide for everyone with the overheating problem on toshiba p100 & Nvidia graphics card. I'm opening a new thread because the kernel patch that was needed in Gutsy is not needed in Hardy anymore. So here goes.

Links to the original info.
[Old thread (Gutsy)]("http://ubuntuforums.org/showthread.php?t=580876")
[URL="http://www.linuxforums.org/forum/peripherals-hardware/96259-toshiba-p100-series-sound-fix-ubuntu.html"]link1
[/URL][link2]("http://ql.homelinux.net/wiki/doku.php?id=ubuntu-7.04:dsdt#le_ventilateur_de_la_gc_nvidia")

**[COLOR=Navy]Step 1 install Intel ASL:[/COLOR]**
```

sudo apt-get install iasl

```[B][COLOR=Navy]
Step 2 backup decompile & edit the dsdt.dsl:
[/COLOR][/B]```
sudo cat /proc/acpi/dsdt > dsdt.dat
iasl -d dsdt.dat
cp dsdt.dsl dsdt.dsl.bak
gedit dsdt.dsl
```
[LIST]
[*]Search for "_T_0" through "_T_7" replace them with "T_0" through "T_7" (withouth the quotes)
[/LIST]

[LIST]
[*]Search for "*PNP0C14" and replace it with "PNP0C14" (again without the quotes)
[/LIST]

[LIST]
[*]Search for "Method (BTST, 0, NotSerialized)" and add "Return(Package(0x02){0x00, 0x00})" just before the closing curly bracket (see below)
[/LIST]
```

Method (BTST, 0, NotSerialized)
            {
                If (\_SB.ECOK)
                {
                    Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
                    Store (\_SB.PCI0.LPCB.EC0.KSWH, Local0)
                    XOr (Local0, 0x01, Local0)
                    Store (\_SB.PCI0.LPCB.EC0.BTHE, Local7)
                    Release (\_SB.PCI0.LPCB.EC0.MUT1)
                    If (Local0)
                    {
                        ShiftLeft (Local7, 0x06, Local6)
                        ShiftLeft (Local7, 0x07, Local7)
                        Or (Local7, Local6, Local1)
                        Or (Local0, Local1, Local2)
                        Return (Local2)
                    }
                    Else
                    {
                        Return (Zero)
                    }
                }
                **[COLOR=Red]Return(Package(0x02){0x00, 0x00})[/COLOR]**
            }


```
[LIST]
[*]Search for "Method (EVNT, 1, NotSerialized)" and add the extra "Return (Zero)" as shown below to Else part of the the "EVNT" method.
[/LIST]

```

            Method (EVNT, 1, NotSerialized)
            {
                While (VZOK)
                {
                    If (LEqual (VZOK, 0x01))
                    {
                        Store (Arg0, VZOK)
                        Notify (\_SB.VALZ, 0x80)
                        Return (Zero)
                    }
                    Else
                    {
                        Sleep (0x05)
                        [COLOR=Red]**Return (Zero)**[/COLOR]
                    }
                }
            }

```**[COLOR=Navy]Step 3 Fix the Nvidia GPU FAN:[/COLOR]**
[COLOR=Red]all of the above was neccessary so you don't get any compile errors when recompiling the dsdt.dsl file (you can check that by going step by step, saving your file and trying to compile it after each step if you want. --> use command "iasl -tc dsdt.dsl" )[/COLOR]


[LIST]
[*]Search for "Method (_REG, 2, NotSerialized)" and add the highlighted code just after where it says "Store (\_SB.PCI0.LPCB.EC0.ACDF, \PWRS)"
[/LIST]
```

Method (_REG, 2, NotSerialized)
                    {
                        If (LEqual (Arg0, 0x03))
                        {
                            Store (Arg1, Local0)
                            If (Local0)
                            {
                                Store (0x01, ECOK)
                                Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
                                Store (\TMOD, \_SB.PCI0.LPCB.EC0.TMOD)
                                Release (\_SB.PCI0.LPCB.EC0.MUT1)
                            }
                            Else
                            {
                                Store (0x00, ECOK)
                            }
                        }

                        If (\_SB.ECOK)
                        {
                            Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
                            If (LEqual (OSYS, 0x07D6))
                            {
                                Store (One, \_SB.PCI0.LPCB.EC0.OSTP)
                                \_SB.PHSR (0x0D, 0x00)
                            }
                            Else
                            {
                                Store (Zero, \_SB.PCI0.LPCB.EC0.OSTP)
                            }

                            Store (0x03, \_SB.PCI0.LPCB.EC0.RG59)
                            Store (\_SB.CIRE, \_SB.PCI0.LPCB.EC0.CIRE)
                            Store (\_SB.PHSR (0x05, 0x00), DOFF)
                            Store (\_SB.PCI0.LPCB.EC0.ACDF, \PWRS)
                            **[COLOR=Red]If (LEqual (OSYS, 0x07D6))[/COLOR]**
                            [B][COLOR=Red]{
                                Store (0x3C, \_SB.PCI0.LPCB.EC0.VTMP)
                            }[/COLOR][/B]            

                            Release (\_SB.PCI0.LPCB.EC0.MUT1)
                        }
                    }

```[COLOR=Navy]**Step 4 recompile & install:**[/COLOR] 
```
iasl -tc dsdt.dsl
```There should be 0 errors and 0 warnings
Now you should have a dsdt.aml file in your working directory. Copy it to /etc/initramfs-tools/ and make sure that you use capital letters "DSDT.aml"
```
sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
sudo dpkg-reconfigure linux-image-$(uname -r)
```**[COLOR=Navy]Step 5 restart and check if its working:[/COLOR]**
You can check your Nvidia cards GPU temperature by installing "nvidia-settings" (under thermal monitor).
```
sudo apt-get install nvidia-settings
```My card runs at a nice 38-42 degrees.

[COLOR=Navy]**Step 6 keep a backup of your dsdt.dsl file:**[/COLOR]
If you don't want to do this again the next time you reinstall ubuntu make a backup copy of the dsdt.dsl file, then you will only have to do Step 4 and 5 next time.

---

### Post by Aramil on 2008-04-30
I m getting the following error.


dsdt.dsl  8740: [*** iASL: Read error on source code temp file ***]
Error    4094 -^ syntax error, unexpected $end


I know nothing of assembly...any help?

---

### Post by Aramil on 2008-04-30
Ok there was a } missing!Everything's ok now!


Btw not fixing this bug in 8.04 is a bit frustrating.They tried to be more vista- like (with all the "security" stuff which I personally dislike) and they forgot to fix some major hardware issues like this one.

I understand that this is open source software (and i  I didnt I wouldnt participate) but I think hardcore devs should take a look at their priorities one more time :)

---

### Post by daimaru on 2008-04-30
@aramil 
Yeah this bug has been a pain, but it seems to be a toshiba satellite p100 series problem. Quite frankly I'm pissed at the toshiba support cause they really don't give a damn. The p100 series (at least the one i got) is a outsourced version that is produced in taiwan or china, can't remember which, but it seems to use the phoenix bios (some cheap *** version of a bios that sucks donky balls and is not used in the other toshibas laptops). I was pretty pissed when  I heard this after I had bought my laptop. I can guarantee that I will never ever buy a toshiba laptop again. Damn tech support sucks ballz.

:lolflag: but nice to hear that the fix worked out for u mate.

EDIT: i'm just saying this about the bios, because toshiba has an extra linux site that deals with problems, drivers etc, but it does not include any support for the PHOENIX bios ... thx alot guys. you should have put that on the sales description!!

---

### Post by linescanner on 2008-05-05
@daimaru,

you are a star.  This has been bugging me for ages.  My P100 now runs without cooking my legs :)

big thanks

---

### Post by Aramil on 2008-05-06
@daimaru

Well I ve got one thing to say.My P100 could not boot from 3 different brands of USB sticks.All over the internet you can find toshiba owners complaining about that...:lolflag:

---

### Post by ocularb0b on 2008-06-07
are these instuctions suited only to toshiba p100's or will this help with other nvidia laptops that run crazy hot?

---

### Post by thideras on 2008-06-07
Thanks Daimaru, I will have to try this on my P100! :D

---

### Post by daimaru on 2008-06-26
> **ocularb0b said:**
> are these instuctions suited only to toshiba p100's or will this help with other nvidia laptops that run crazy hot?

will only work on p100

---

### Post by jmit038 on 2008-08-20
Thank you ! I am watching my laptop cool down while it's running !!!! wont be able to use it to make this nemore tho lol :popcorn:

---

### Post by mike.gillan on 2008-08-28
Thank you very much for the well-written and easy to follow how-to. My company is slowly switching to Ubuntu, and I'm the only one with a P100... now nobody can laugh at me for having a laptop which shuts itself off twice a day!!! :guitar:

---

### Post by jessi3k3 on 2008-09-06
Thanks for the guide. I had done this a year ago but i couldnt find the original guide that i used. I found this one instead and it was just as good. Now everything is running fine on my P105 in linux. Thanks! No more burning gpu!

---

### Post by Sacob on 2008-10-05
can't you just give me the dsdt.dsl file? i have got several compilation errors and my p100 is still burning :(

---

### Post by Sacob on 2008-10-12
nobody?

---

### Post by rax_m on 2008-11-11
Daimaru - Remember me from the old Gutsy thread ;) 
Did you manage to get your external mic working on Hardy? 
That's one thing that doesn't seem to work for me.. hence I'm still using Gutsy. 

I still have to try editing /etc/modprobe.d/asla-base ...  

Sacob - someone could give you the DSDT but if your models differ even slightly it might mess something up on your lappie. Rather do it yourself.

Thanks

---

### Post by rax_m on 2008-11-11
Ignore my last question... 
I found the issue. 

It seems the mic and capture inputs were all set to the lowest setting. I installed gnome-alsamixer and changed the settings according to this post by ruppertus: 
[http://www.linuxquestions.org/questions/linux-hardware-18/microphone-doesnt-work-intel-hd-audio-619337/](http://www.linuxquestions.org/questions/linux-hardware-18/microphone-doesnt-work-intel-hd-audio-619337/)

---

### Post by Sacob on 2008-11-13
Is this problem fixed in 8.10 version?

---

### Post by daimaru on 2008-11-21
> **rax_m said:**
> Daimaru - Remember me from the old Gutsy thread ;) 

Sorry for the late reply::: been on vacation

hi rax_m sure i still remember u without ur help i would have never found the answer to this problem. Thanks again mate. I did some research and I now know that toshiba used a bunch of faulty nvidia gpus in the p100 series. Nvidia provided a special driver for those laptops that keeps the fan running way more than on normal models. this is kinda sad cause it explains why the battery life on my p100 is so low. 

Just to clarify this is not a Ubuntu or linux problem at all. if you install any nvidia driver not provided by your laptops manufacturer (for example the newest one from the nvidia website) your laptop's GPU will fry even under windows ( tested under XP). 

The manufacturers made a deal with nvidia so the only drivers you can use are the ones provided by your laptop manufacturer. They basically did the quick fix thing we did under ubuntu and applied it to windows. 

I tried using a new driver recently and it almost fried my gpu ... sad sad sad . they should give us back our money : ) 

Oh and regarding the question by [COLOR=Red]Sacob[/COLOR] if this fix is still needed under 8.10. I would guess yes because of the above mentioned facts. But  I have not yet installed 8.10 on my laptop. Going to do that this week though. Hope the fix or a modified version of it still works. 

Will post my findings. 

greets all.

---

### Post by daimaru on 2008-11-21
> **Sacob said:**
> can't you just give me the dsdt.dsl file? i have got several compilation errors and my p100 is still burning :(
Hi Sacob, as rax_m already mentioned the dstd.dsl file will probably not be too usefull for your laptop unless you have the exact same model as someone else in this thread. 

Its worth a try post your model number (mine is p100-239 also called PSPA6E) .

Once I get 8.10 running on my laptop and verified that the fix is still working I could attach my dsdt.dsl file, but be careful using it, if your laptop is a different model.

Cheers

---

### Post by daimaru on 2008-11-25
Can confirm that fix is still needed (wyh? see previous posts) 
Can confirm fix still works.

Just installed 8.10 on my p100-239 applied fix and its running @ 50C° .

---

### Post by twiz86 on 2008-11-29
I just used this on my p105 and it took my temps from 116C to 55C. Thanks man, you kick ***.

---

### Post by vulturesrow on 2008-12-10
> **twiz86 said:**
> I just used this on my p105 and it took my temps from 116C to 55C. Thanks man, you kick ***.


=D>

This post should 100 percent absolutely be stickied. I have a P105-S921 and this was literally a life saver. I can say one thing for certain, I will never buy another Tobshiba laptop. This one has had more problems than I can remember. Dont even ask me how much time and effort Ive spent on the DC jack and power supply. 

But seriously, how does a post get stickied? Because this one absolutely needs to for several reasons:

1. Not distro dependent.
2. Affects a fairly popular line of laptop computers. 
3. Lots of people ask about this particular problem.

Anyone?


EDIT: How the heck do I do the thank you thing for the original post? (yes Im a dunce)

---

### Post by daimaru on 2008-12-14
thanks vulturesrow for adding your laptop model name. Hope others will do the same. I added it to the first post, wanted to make a list of toshiba laptops that this works on (confirmed by user).

cheers

---

### Post by heaven_weapon on 2009-01-21
hi i hope someone can help me
i have a toshiba p105-s9312 with a geforce go 7900gs gpu
i did every step of this guide with 0 errors, recompiled, etc, but it doesn't work, maybe doesn't work with my model, does anybody know something about it?

---

### Post by daimaru on 2009-02-03
> **heaven_weapon said:**
> hi i hope someone can help me
i have a toshiba p105-s9312 with a geforce go 7900gs gpu
i did every step of this guide with 0 errors, recompiled, etc, but it doesn't work, maybe doesn't work with my model, does anybody know something about it?

EDIT: sorry I don't have the GS card so disregard what I posted. 
hi, 
that is kind of weird, because i have the same card NVIDIA GeForce Go 7900 PCI Express x16

in my satellite p100-239. and it works for me.

---

### Post by some_dude on 2009-02-13
> **heaven_weapon said:**
> hi i hope someone can help me
i have a toshiba p105-s9312 with a geforce go 7900gs gpu
i did every step of this guide with 0 errors, recompiled, etc, but it doesn't work, maybe doesn't work with my model, does anybody know something about it?

Did you make sure you saved the new dsdt.dsl over the old one?  I know it sounds redundant but the first time I went through the process, I made the changes using the text editor, then clicked save and left the editor open while I proceeded to the final steps.  Nothing seemed to go wrong (and it didn't fix the problem either). I think the save was sent to the buffer, but didn't go through because it was not full enough and/or because the text editor was still open.

What I did to ensure that the old dsdt.dsl was written was save it to a new directory (for me, the desktop) then I know it's the changed one, then I entered:
cd Desktop

in the terminal to change the current directory and then proceeded with the rest.

That aside, the fix works!!!:) I have a Toshiba P100 (pspa3c-ma202c) with geforce go 7600 128 mb and the fan works now! Running at 50 - 55 degrees celsius idle down from like 70.  

If anyone knows how to get the gpu fan to work in vista, Please let me know as I haven't found a fix anywhere and it seemed simple enough!

---

### Post by geoffd123 on 2009-04-06
Fantastic, thank you for working this out.  My machine had reached a stage where it powered off and when I restarted was powering off before I managed to get back to where I was!

After the fix it is running at a nice 40C.

So I can confirm that this patch works on a P100-208--PSPA3E.

Thanks once again
Geoff

---

### Post by daimaru on 2009-04-08
nice to hear it works

---

### Post by enginy88 on 2009-04-24
yes, 9,04 is out!

it's a pleasure to anounce the fix is also works on 9,04 !!!

I was saved dsdt.dsl file when i was using 8,10 so i only did recompile and install step (step 4)

And it works like a charm with my toshiba p100-324 (PSPA6E) with nvidia Geforce go 7900 gs) My core temperature goes from 100 to 50 degrees..

---

### Post by daimaru on 2009-05-04
good to know haven't upgraded yet, but will now.

---

### Post by enginy88 on 2009-05-06
what do you mean with "haven't updated" ???? 
is there a change in a few days???

---

### Post by jazzedmurf on 2009-07-21
Any information as to whether this works on my model? 

Specs:

P100 - ST9412
Intel Centrino Duo @ 2.00GHz
4 GB of RAM
Nvidia GeForce Go 7900 GTX (512 mb)

Like the original thread states, I too am experiencing severe GPU overheating due to the GPU fan not operating correctly. I'm going to try this fix on 9.04 tomorrow--I've been dying to get Linux on my laptop, but the distros so far have been unkind. 

Any help is appreciated!
[B]
UPDATE: I tried this today--I'm a complete Linux noob--and it didn't go my way the first time. But the second time worked like a charm. My laptop went from a searing 100+ degrees to under 60. THANK YOU SO MUCH! This fix works on the P100-ST9412 (GeForce Go 7900 GTX 512mb) on 9.04 Jaunty Jack. Thanks again![/B]

---

### Post by daimaru on 2009-07-30
just confirming that it work on my new jaunty laptop install (not related to my desktop sig). :)

---

### Post by tommck on 2009-08-14
Just an FYI:  I tried this with Karmic Koala on a P105-S9337 and it did NOT work.

:(

---

### Post by MacWomble on 2009-10-12
hallo,

My PC is an Satellite P100-191 with UBUNTU 9.10 Beta.
Without this patch the GPU fan never runs, with this patch it runs only when temperature is over 124 C :-( 

So my card is over 100 C all the time.
How can I solve this?

Regards Klaus

---

### Post by UNaX on 2009-10-14
After the upgrade to Ubuntu 9.10 Beta I got the same problem with a Toshiba P100-491 (PSPAME).My card is over 90 C all the time.

Need also some help to solve this.
THX

---

### Post by krantix on 2009-10-23
same problem here on p100 pspage, with karmic it DOES NOT WORK.

---

### Post by krantix on 2009-10-23
I've been using the dsdt trick for ages (since I bought the laptop 2 years ago) and it always worked, but now with karmic it's somehow broken!!!

one option in the past was to boot with the "acpi=off" added to the boot line to make sure you wouldn't fry your card... but it's definitely not a sustainable solution.

---

### Post by haouariano on 2009-11-20
Please help !!!  my Nvidia 7600 is burning :(  **70°C** and more
After changing my dsdt using the steps described on the guide [here]("http://ubuntuforums.org/showthread.php?t=771223"), recompiling shows 8 errors:
_________________________________________________
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  2158:                                         Name (_T_1, 0x00)
Error    4081 -                             Use of reserved word ^  (_T_1)

dsdt.dsl  2192:                                             Name (_T_2, 0x00)
Error    4081 -                                 Use of reserved word ^  (_T_2)

dsdt.dsl  2226:                                                 Name (_T_3, 0x00)
Error    4081 -                                     Use of reserved word ^  (_T_3)

dsdt.dsl  2274:                                                     Name (_T_4, 0x00)
Error    4081 -                                         Use of reserved word ^  (_T_4)

dsdt.dsl  2308:                                                         Name (_T_5, 0x00)
Error    4081 -                                             Use of reserved word ^  (_T_5)

dsdt.dsl  2356:                                                             Name (_T_6, 0x00)
Error    4081 -                                                 Use of reserved word ^  (_T_6)

dsdt.dsl  7153:                     } 2158:
Error    4094 -                          ^ syntax error, unexpected PARSEOP_INTEGER

dsdt.dsl  7153:                     } 2158:
Error    4094 -                           ^ Invalid character (0x3A), expecting ASL keyword or name

ASL Input:  dsdt.dsl - 8741 lines, 324595 bytes, 3506 keywords
Compilation complete. 8 Errors, 0 Warnings, 0 Remarks, 1242 Optimizations
___________________________
Did any one knows what kind of errors are these? 
and how may I correct them?

**I'm using a Thoshiba P100-284 and Ubuntu 8.04 (Hardy)**

Thanks

---

### Post by daimaru on 2009-12-06
> **haouariano said:**
> 
After changing my dsdt using the steps described on the guide [here]("http://ubuntuforums.org/showthread.php?t=771223"), recompiling shows 8 errors:
_________________________________________________
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  2158:                                         Name (_T_1, 0x00)
Error    4081 -                             Use of reserved word ^  (_T_1)

dsdt.dsl  2192:                                             Name (_T_2, 0x00)
Error    4081 -                                 Use of reserved word ^  (_T_2)
...

looks like you did not  rename "_T_0" through "_T_7" to "T_0" through "T_7"

---

### Post by daimaru on 2009-12-06
I just updated my ubuntu 9.04 to 9.10 (9.04 had the fix applied) I did not have to do anything it still worked with ubuntu 9.10. Have not yet tried if it does not work on a clean install of 9.10. 

can anyone confirm that it works for ubuntu 9.10 clean install ?

---

### Post by haouariano on 2009-12-08
> **daimaru said:**
> looks like you did not  rename "_T_0" through "_T_7" to "T_0" through "T_7"

ok but I think that I renamed every "_T_0" with "T_0" and every "_T_7" with "T_7" is that wrong?? :?

---

### Post by rax_m on 2009-12-13
Hi all,

I was wondering if anyone has managed to test the new BIOS 4.7 with Linux? 

From the Toshiba website:
Version 4.70 - 2009-02-18
    * Per new spec., the BIOS password is copied to EEPROM and the CMOS and EEPROM password values are compared during POST. If the values are different, the BIOS will copy the EEPROM value to CMOS.
[COLOR="Red"]    * Improved: VGA Fan did not work properly.[/COLOR]

thanks
rax

---

### Post by lucag on 2009-12-14
> **rax_m said:**
> Hi all,

I was wondering if anyone has managed to test the new BIOS 4.7 with Linux? 

From the Toshiba website:
Version 4.70 - 2009-02-18
    * Per new spec., the BIOS password is copied to EEPROM and the CMOS and EEPROM password values are compared during POST. If the values are different, the BIOS will copy the EEPROM value to CMOS.
[COLOR=Red]    * Improved: VGA Fan did not work properly.[/COLOR]

thanks
rax

I have a P100 suffering the same problem, solved with 9.04 and the pach described in this thread. The problem appeared again with 9.10 as observed by others.

Now I have to add another piece of information: after update to kernel 2.31.16 the fan started working again and the overheating problem was over. For few hours only, because then I found bios 4.80 from toshiba, which is new and adds the possibility to enable virtualization. I could not refrain myself from updating the bios too .. and I have again the overheating :-( I also have later updated the kernel to 2.31.17 but nothing changed. Now I may run Linux in virtualbox under XP ... or with acpi=off.

---

### Post by edwardtilbury on 2009-12-18
Yeah, Toshiba is horrible.. I have the same problem on my P105-S9339... 

I don't care if my finger pad thing doesn't work or if my winmodem doesn't work.. but I absolutely need a working GPU!

9.04 Didn't work, constantly overheated.. maybe 9.10 or the next version will catch it.

---

### Post by ominouswanderer on 2010-01-05
Please Help!!! I am _**desperately **_trying to get this to work on a p105s9722 and using 9.10 and bios version 3.70 and get major compile errors. Following the instructions word for word gives me the following errors...
  
dsdt.dsl   472:                     Notify (\_SB.PCI0.RP03, 0x00)
Error    4062 -                    Object does not exist ^  (\_SB.PCI0.RP03)

dsdt.dsl   476:                     Store (0x01, \_SB.PCI0.RP03.HPCS)
Error    4062 -                              Object does not exist ^  (\_SB.PCI0.RP03.HPCS)

dsdt.dsl   480:             If (LAnd (LEqual (RP4D, 0x00), \_SB.PCI0.RP04.HPCS))
Error    4062 -                                        Object does not exist ^  (\_SB.PCI0.RP04.HPCS)

dsdt.dsl   482:                 If (\_SB.PCI0.RP04.PDC4)
Error    4062 -                 Object does not exist ^  (\_SB.PCI0.RP04.PDC4)

dsdt.dsl   484:                     Store (0x01, \_SB.PCI0.RP04.PDC4)
Error    4062 -                              Object does not exist ^  (\_SB.PCI0.RP04.PDC4)

dsdt.dsl   485:                     Store (0x01, \_SB.PCI0.RP04.HPCS)
Error    4062 -                              Object does not exist ^  (\_SB.PCI0.RP04.HPCS)

dsdt.dsl   486:                     Notify (\_SB.PCI0.RP04, 0x00)
Error    4062 -                    Object does not exist ^  (\_SB.PCI0.RP04)

dsdt.dsl   490:                     Store (0x01, \_SB.PCI0.RP04.HPCS)
Error    4062 -                              Object does not exist ^  (\_SB.PCI0.RP04.HPCS)

dsdt.dsl   494:             If (LAnd (LEqual (RP5D, 0x00), \_SB.PCI0.RP05.HPCS))
Error    4062 -                                        Object does not exist ^  (\_SB.PCI0.RP05.HPCS)

dsdt.dsl   496:                 If (\_SB.PCI0.RP05.PDC5)
Error    4062 -                 Object does not exist ^  (\_SB.PCI0.RP05.PDC5)

dsdt.dsl   498:                     Store (0x01, \_SB.PCI0.RP05.PDC5)
Error    4062 -                              Object does not exist ^  (\_SB.PCI0.RP05.PDC5)

dsdt.dsl   499:                     Store (0x01, \_SB.PCI0.RP05.HPCS)
Error    4062 -                              Object does not exist ^  (\_SB.PCI0.RP05.HPCS)

dsdt.dsl   500:                     Notify (\_SB.PCI0.RP05, 0x00)
Error    4062 -                    Object does not exist ^  (\_SB.PCI0.RP05)

dsdt.dsl   504:                     Store (0x01, \_SB.PCI0.RP05.HPCS)
Error    4062 -                              Object does not exist ^  (\_SB.PCI0.RP05.HPCS)

dsdt.dsl   508:             If (LAnd (LEqual (RP6D, 0x00), \_SB.PCI0.RP06.HPCS))
Error    4062 -                                        Object does not exist ^  (\_SB.PCI0.RP06.HPCS)

dsdt.dsl   510:                 If (\_SB.PCI0.RP06.PDC6)
Error    4062 -                 Object does not exist ^  (\_SB.PCI0.RP06.PDC6)

dsdt.dsl   512:                     Store (0x01, \_SB.PCI0.RP06.PDC6)
Error    4062 -                              Object does not exist ^  (\_SB.PCI0.RP06.PDC6)

dsdt.dsl   513:                     Store (0x01, \_SB.PCI0.RP06.HPCS)
Error    4062 -                              Object does not exist ^  (\_SB.PCI0.RP06.HPCS)

dsdt.dsl   514:                     Notify (\_SB.PCI0.RP06, 0x00)
Error    4062 -                    Object does not exist ^  (\_SB.PCI0.RP06)

dsdt.dsl   518:                     Store (0x01, \_SB.PCI0.RP06.HPCS)
Error    4062 -                              Object does not exist ^  (\_SB.PCI0.RP06.HPCS)

dsdt.dsl   526:             If (\_SB.ECOK)
Error    4062 -   Object does not exist ^  (\_SB.ECOK)

dsdt.dsl   528:                 Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
Error    4062 -                          Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl   529:                 Store (DTSP, \_SB.PCI0.LPCB.EC0.DESP)
Error    4062 -                              Object does not exist ^  (\_SB.PCI0.LPCB.EC0.DESP)

dsdt.dsl   530:                 Release (\_SB.PCI0.LPCB.EC0.MUT1)
Error    4062 -                          Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl   536:             Notify (\_SB.PCI0.USB1, 0x02)
Error    4062 -            Object does not exist ^  (\_SB.PCI0.USB1)

dsdt.dsl   541:             Notify (\_SB.PCI0.USB2, 0x02)
Error    4062 -            Object does not exist ^  (\_SB.PCI0.USB2)

dsdt.dsl   549:                 Notify (\_SB.PCI0.HDEF, 0x02)
Error    4062 -                Object does not exist ^  (\_SB.PCI0.HDEF)

dsdt.dsl   555:             Store (0x20, \_SB.PCI0.SBUS.HSTS)
Error    4062 -                      Object does not exist ^  (\_SB.PCI0.SBUS.HSTS)

dsdt.dsl   560:             If (\_SB.PCI0.RP01.PSP1)
Error    4062 -             Object does not exist ^  (\_SB.PCI0.RP01.PSP1)

dsdt.dsl   562:                 Store (0x01, \_SB.PCI0.RP01.PSP1)
Error    4062 -                          Object does not exist ^  (\_SB.PCI0.RP01.PSP1)

dsdt.dsl   563:                 Store (0x01, \_SB.PCI0.RP01.PMCS)
Error    4062 -                          Object does not exist ^  (\_SB.PCI0.RP01.PMCS)

dsdt.dsl   564:                 Notify (\_SB.PCI0.RP01, 0x02)
Error    4062 -                Object does not exist ^  (\_SB.PCI0.RP01)

dsdt.dsl   567:             If (\_SB.PCI0.RP02.PSP2)
Error    4062 -             Object does not exist ^  (\_SB.PCI0.RP02.PSP2)

dsdt.dsl   569:                 Store (0x01, \_SB.PCI0.RP02.PSP2)
Error    4062 -                          Object does not exist ^  (\_SB.PCI0.RP02.PSP2)

dsdt.dsl   570:                 Store (0x01, \_SB.PCI0.RP02.PMCS)
Error    4062 -                          Object does not exist ^  (\_SB.PCI0.RP02.PMCS)

dsdt.dsl   571:                 Notify (\_SB.PCI0.RP02, 0x02)
Error    4062 -                Object does not exist ^  (\_SB.PCI0.RP02)

dsdt.dsl   574:             If (\_SB.PCI0.RP03.PSP3)
Error    4062 -             Object does not exist ^  (\_SB.PCI0.RP03.PSP3)

dsdt.dsl   576:                 Store (0x01, \_SB.PCI0.RP03.PSP3)
Error    4062 -                          Object does not exist ^  (\_SB.PCI0.RP03.PSP3)

dsdt.dsl   577:                 Store (0x01, \_SB.PCI0.RP03.PMCS)
Error    4062 -                          Object does not exist ^  (\_SB.PCI0.RP03.PMCS)

dsdt.dsl   578:                 Notify (\_SB.PCI0.RP03, 0x02)
Error    4062 -                Object does not exist ^  (\_SB.PCI0.RP03)

dsdt.dsl   584:             Notify (\_SB.PWRB, 0x02)
Error    4062 -       Object does not exist ^  (\_SB.PWRB)

dsdt.dsl   589:             Notify (\_SB.PCI0.USB3, 0x02)
Error    4062 -            Object does not exist ^  (\_SB.PCI0.USB3)

dsdt.dsl   594:             Notify (\_SB.PCI0.USB7, 0x02)
Error    4062 -            Object does not exist ^  (\_SB.PCI0.USB7)

dsdt.dsl   599:             Notify (\_SB.PCI0.USB4, 0x02)
Error    4062 -            Object does not exist ^  (\_SB.PCI0.USB4)

dsdt.dsl   622:                         Notify (\_SB.PCI0, 0x00)
Error    4062 -                   Object does not exist ^  (\_SB.PCI0)

dsdt.dsl   626:                         Notify (\_SB.PCI0.GFX0, 0x00)
Error    4062 -                        Object does not exist ^  (\_SB.PCI0.GFX0)

dsdt.dsl   632:                 Notify (\_SB.PCI0.GFX0, 0x80)
Error    4062 -                Object does not exist ^  (\_SB.PCI0.GFX0)

dsdt.dsl   640:                 Notify (\_SB.PCI0.GFX0, 0x81)
Error    4062 -                Object does not exist ^  (\_SB.PCI0.GFX0)

dsdt.dsl  7305:         Return(Package(0x02){0x00, 0x00})
Error    4094 -              ^ syntax error, unexpected PARSEOP_RETURN

dsdt.dsl  7338:                         Notify (\_SB.VALZ, 0x80)
Error    4062 -                   Object does not exist ^  (\_SB.VALZ)

dsdt.dsl  7353:                     Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
Error    4062 -                              Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7354:                     Store (\_SB.PCI0.LPCB.EC0.VEVT, Local0)
Error    4062 -                            Object does not exist ^  (\_SB.PCI0.LPCB.EC0.VEVT)

dsdt.dsl  7355:                     Release (\_SB.PCI0.LPCB.EC0.MUT1)
Error    4062 -                              Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7363:                         Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
Error    4062 -                                  Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7364:                         Store (\_SB.PCI0.LPCB.EC0.FEVT, Local0)
Error    4062 -                                Object does not exist ^  (\_SB.PCI0.LPCB.EC0.FEVT)

dsdt.dsl  7365:                         Release (\_SB.PCI0.LPCB.EC0.MUT1)
Error    4062 -                                  Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7373:                             Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
Error    4062 -                                      Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7374:                             Store (\_SB.PCI0.LPCB.EC0.NEVT, Local0)
Error    4062 -                                    Object does not exist ^  (\_SB.PCI0.LPCB.EC0.NEVT)

dsdt.dsl  7375:                             Release (\_SB.PCI0.LPCB.EC0.MUT1)
Error    4062 -                                      Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7665:                             Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
Error    4062 -                                      Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7666:                             Store (\_SB.PCI0.LPCB.EC0.KSWH, Local0)
Error    4062 -                                    Object does not exist ^  (\_SB.PCI0.LPCB.EC0.KSWH)

dsdt.dsl  7668:                             Store (\_SB.PCI0.LPCB.EC0.RFST, Local1)
Error    4062 -                                    Object does not exist ^  (\_SB.PCI0.LPCB.EC0.RFST)

dsdt.dsl  7670:                             Release (\_SB.PCI0.LPCB.EC0.MUT1)
Error    4062 -                                      Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7683:                                 \_SB.PHSR (0x0C, 0x23)
Error    4062 -                   Object does not exist ^  (\_SB.PHSR)

dsdt.dsl  7690:                                     \_SB.PHSR (0x0C, 0x24)
Error    4062 -                       Object does not exist ^  (\_SB.PHSR)

dsdt.dsl  7706:                                 Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
Error    4062 -                                          Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7707:                                 Store (\_SB.PCI0.LPCB.EC0.TPAD, Local0)
Error    4062 -                                        Object does not exist ^  (\_SB.PCI0.LPCB.EC0.TPAD)

dsdt.dsl  7709:                                 Release (\_SB.PCI0.LPCB.EC0.MUT1)
Error    4062 -                                          Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7717:                                     \_SB.PHSR (0x0C, 0x5A)
Error    4062 -                       Object does not exist ^  (\_SB.PHSR)

dsdt.dsl  7724:                                         \_SB.PHSR (0x0C, 0x5B)
Error    4062 -                           Object does not exist ^  (\_SB.PHSR)

dsdt.dsl  7740:                                     \_SB.PHSR (0x0E, 0x00)
Error    4062 -                       Object does not exist ^  (\_SB.PHSR)

dsdt.dsl  7747:                                         \_SB.PHSR (0x0E, 0x01)
Error    4062 -                           Object does not exist ^  (\_SB.PHSR)

dsdt.dsl  7754:                                             \_SB.PHSR (0x0E, 0x02)
Error    4062 -                               Object does not exist ^  (\_SB.PHSR)

dsdt.dsl  7770:                                         Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
Error    4062 -                                                  Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7771:                                         Store (\_SB.PCI0.LPCB.EC0.TMOD, Local0)
Error    4062 -                                                Object does not exist ^  (\_SB.PCI0.LPCB.EC0.TMOD)

dsdt.dsl  7772:                                         Release (\_SB.PCI0.LPCB.EC0.MUT1)
Error    4062 -                                                  Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7781:                                             Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
Error    4062 -                                                      Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7782:                                             Store (0x00, \_SB.PCI0.LPCB.EC0.TMOD)
Error    4062 -                                                          Object does not exist ^  (\_SB.PCI0.LPCB.EC0.TMOD)

dsdt.dsl  7783:                                             Release (\_SB.PCI0.LPCB.EC0.MUT1)
Error    4062 -                                                      Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7784:                                             \_SB.PHSR (0x0B, 0x00)
Error    4062 -                               Object does not exist ^  (\_SB.PHSR)

dsdt.dsl  7791:                                                 Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
Error    4062 -                                                          Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7792:                                                 Store (0x01, \_SB.PCI0.LPCB.EC0.TMOD)
Error    4062 -                                                              Object does not exist ^  (\_SB.PCI0.LPCB.EC0.TMOD)

dsdt.dsl  7793:                                                 Release (\_SB.PCI0.LPCB.EC0.MUT1)
Error    4062 -                                                          Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7794:                                                 \_SB.PHSR (0x0B, 0x01)
Error    4062 -                                   Object does not exist ^  (\_SB.PHSR)

dsdt.dsl  7810:                                             If (LEqual (\_SB.ENSR, 0x02))
Error    4062 -                                           Object does not exist ^  (\_SB.ENSR)

dsdt.dsl  7875:                                                         \_SB.PHSR (0x0A, 0xC0)
Error    4062 -                                           Object does not exist ^  (\_SB.PHSR)

dsdt.dsl  7883:                                                             \_SB.PHSR (0x0A, 0x40)
Error    4062 -                                               Object does not exist ^  (\_SB.PHSR)

dsdt.dsl  7891:                                                                 \_SB.PHSR (0x0A, 0x80)
Error    4062 -                                                   Object does not exist ^  (\_SB.PHSR)

dsdt.dsl  7899:                                                                     \_SB.PHSR (0x0A, 0x00)
Error    4062 -                                                       Object does not exist ^  (\_SB.PHSR)

dsdt.dsl  7991:                 Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
Error    4062 -                          Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  7992:                 Store (DerefOf (Index (STBC, 0x01)), \_SB.PCI0.LPCB.EC0.VTMP)
Error    4062 -                                                      Object does not exist ^  (\_SB.PCI0.LPCB.EC0.VTMP)

dsdt.dsl  7993:                 Release (\_SB.PCI0.LPCB.EC0.MUT1)
Error    4062 -                          Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  8095:                     Acquire (\_SB.PSMX, 0xFFFF)
Error    4062 -                Object does not exist ^  (\_SB.PSMX)

dsdt.dsl  8096:                     Store (0x91, BCMD)
Error    4062 -               Object does not exist ^  (BCMD)

dsdt.dsl  8097:                     Store (Arg0, DID)
Error    4062 -              Object does not exist ^  (DID_)

dsdt.dsl  8098:                     Store (Arg1, INF)
Error    4062 -              Object does not exist ^  (INF_)

dsdt.dsl  8099:                     Store (Zero, SMIC)
Error    4062 -               Object does not exist ^  (SMIC)

dsdt.dsl  8100:                     Store (DID, Local0)
Error    4062 -        Object does not exist ^  (DID_)

dsdt.dsl  8101:                     Release (\_SB.PSMX)
Error    4062 -                Object does not exist ^  (\_SB.PSMX)

dsdt.dsl  8337:                         Store (OWNS, Q512)
Error    4062 -             Object does not exist ^  (OWNS)

dsdt.dsl  8360:                     Store (Arg1, OWNS)
Error    4062 -               Object does not exist ^  (OWNS)

dsdt.dsl  8365:                         Store (OWNS, Q512)
Error    4062 -             Object does not exist ^  (OWNS)

dsdt.dsl  8381:                         Store (OWNS, Q512)
Error    4062 -             Object does not exist ^  (OWNS)

dsdt.dsl  8391:                         Store (OWNS, Q512)
Error    4062 -             Object does not exist ^  (OWNS)

dsdt.dsl  8414:                     Store (Arg1, OWNS)
Error    4062 -               Object does not exist ^  (OWNS)

dsdt.dsl  8419:                         Store (OWNS, Q512)
Error    4062 -             Object does not exist ^  (OWNS)

dsdt.dsl  8435:                         Store (OWNS, Q512)
Error    4062 -             Object does not exist ^  (OWNS)

dsdt.dsl  8451:                     Store (OWNS, Q512)
Error    4062 -         Object does not exist ^  (OWNS)

dsdt.dsl  8456:                     Store (Arg1, OWNS)
Error    4062 -               Object does not exist ^  (OWNS)

dsdt.dsl  8471:                     Store (OWNS, Q512)
Error    4062 -         Object does not exist ^  (OWNS)

dsdt.dsl  8476:                     Store (Arg1, OWNS)
Error    4062 -               Object does not exist ^  (OWNS)

dsdt.dsl  8491:                     Store (OWNS, Q512)
Error    4062 -         Object does not exist ^  (OWNS)

dsdt.dsl  8496:                     Store (Arg1, OWNS)
Error    4062 -               Object does not exist ^  (OWNS)

dsdt.dsl  8511:                     Store (OWNS, Q512)
Error    4062 -         Object does not exist ^  (OWNS)

dsdt.dsl  8516:                     Store (Arg1, OWNS)
Error    4062 -               Object does not exist ^  (OWNS)

dsdt.dsl  8531:                     Store (OWNS, Q512)
Error    4062 -         Object does not exist ^  (OWNS)

dsdt.dsl  8536:                     Store (Arg1, OWNS)
Error    4062 -               Object does not exist ^  (OWNS)

dsdt.dsl  8551:                     Store (OWNS, Q512)
Error    4062 -         Object does not exist ^  (OWNS)

dsdt.dsl  8556:                     Store (Arg1, OWNS)
Error    4062 -               Object does not exist ^  (OWNS)

dsdt.dsl  8563:                     Store (OWNS, Q512)
Error    4062 -         Object does not exist ^  (OWNS)

dsdt.dsl  8569:                     Store (Arg1, OWNS)
Error    4062 -               Object does not exist ^  (OWNS)

dsdt.dsl  8576:                     Store (OWNS, Q512)
Error    4062 -         Object does not exist ^  (OWNS)

dsdt.dsl  8586:                     Store (OWNS, Q512)
Error    4062 -         Object does not exist ^  (OWNS)

dsdt.dsl  8591:                     Store (Arg1, OWNS)
Error    4062 -               Object does not exist ^  (OWNS)

dsdt.dsl  8598:                     Store (OWNS, Q512)
Error    4062 -         Object does not exist ^  (OWNS)

dsdt.dsl  8705:                     If (\_SB.ECOK)
Error    4062 -           Object does not exist ^  (\_SB.ECOK)

dsdt.dsl  8707:                         Acquire (\_SB.PCI0.LPCB.EC0.MUT1, 0xFFFF)
Error    4062 -                                  Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  8708:                         Store (\_SB.PCI0.LPCB.EC0.CTMP, Local0)
Error    4062 -                                Object does not exist ^  (\_SB.PCI0.LPCB.EC0.CTMP)

dsdt.dsl  8709:                         Release (\_SB.PCI0.LPCB.EC0.MUT1)
Error    4062 -                                  Object does not exist ^  (\_SB.PCI0.LPCB.EC0.MUT1)

dsdt.dsl  8738:     Name
Error    4094 -        ^ syntax error, unexpected PARSEOP_NAME, expecting $end

ASL Input:  dsdt.dsl - 8739 lines, 324527 bytes, 3506 keywords
Compilation complete. 187 Errors, 0 Warnings, 0 Remarks, 364 Optimizations



Any help would be greatly appreciated. I need to get this machine working again!

Thanks in advance!

---

### Post by daimaru on 2010-01-23
Bios: Phoenix version 4.80 (don't know if this makes any difference, but since before i compiled kernel I tried all kinds of other stuff I also updated my bios)
Graphics: Nvidia Go 7900 GS

**Fixed my p100-239 running ubuntu 9.10**. In order to do this you will need to _recompile your kernel from source_, since somehow the kernels > 2.6.30 do not override the custom dsdt settings used with initramfs. They revert back to the bios DSDT table for the information and as we already know that is faulty with the toshiba p100 series laptops.

I followed [cyberey66]("http://ubuntuforums.org/member.php?u=849910") post [here]("http://ubuntuforums.org/showthread.php?t=1341580") as well as [this info]("http://www.lesswatts.org/projects/acpi/overridingDSDT.php") and this [help]("https://help.ubuntu.com/community/Kernel/Compile") .. to get my dsdt.hex file comiled into the kernel. It seems to work fine since while i was compiling my gpu temperature was at 100 - 106° max. And after reboot and while writing this my GPU is running at 54°. So this seems to work, but I have not yet tested if other issues arise with this (besides the fact that I will have to recompile my kernel when a new kernel gets released).

This may not be a perfect solution, but I think it beats frying my legs with a 100°+ gpu temp. 

I am looking into flashing my bios's dsdt information with the altered (fixed) dsdt using the Phoenix BIOS Editor so as to skip ever having to redo all this stuff. If anyone has worked with this before help would be appreciated.

---

### Post by daimaru on 2010-01-24
ok eventhough it works, I now have problems with dpkg build while installing new applications. But I guess this is due to my inexperience building custom kernels. I will try to build another kernel again, since the dsdt stuff did seem to work. Its just the other little things that annoy now. At least I can experiement now without my laptop overheating.

---

### Post by daimaru on 2010-01-25
Nevermind that kernel compile stuff. It works out of the box now. No dsdt stuff needed anymore. Just do clean install of 9.10 activate nvidia driver v185 and your good to go. At least my Toshiba Satellite P100-239 (Modell Nr.                    :                                            PSPA6E-03F01FGR) with the newest Bios installed (4.80) is not overheating anymore. Thank god this is fixed now hope it stays this way in the future.

---

### Post by lucag on 2010-02-09
> **daimaru said:**
> Nevermind that kernel compile stuff. It works out of the box now. No dsdt stuff needed anymore. Just do clean install of 9.10 activate nvidia driver v185 and your good to go. At least my Toshiba Satellite P100-239 (Modell Nr.                    :                                            PSPA6E-03F01FGR) with the newest Bios installed (4.80) is not overheating anymore. Thank god this is fixed now hope it stays this way in the future.

Unfortunately I cannot confirm this on my P100. I've done a fresh install of 9.10 and it doesn't work. Same drivers (185) , same bios (4.80) tesetd kernel updates 2.31.14, 17 and 19.  If I uninstall the proprietary drivers the cooling fan works at high temperature, with the proprietary drivers the temperature exceeds 100°C and the fan do not start at all.

---

### Post by daimaru on 2010-02-25
> **lucag said:**
> Unfortunately I cannot confirm this on my P100. I've done a fresh install of 9.10 and it doesn't work. Same drivers (185) , same bios (4.80) tesetd kernel updates 2.31.14, 17 and 19.  If I uninstall the proprietary drivers the cooling fan works at high temperature, with the proprietary drivers the temperature exceeds 100°C and the fan do not start at all.
try compiling the dsdt stuff into a custom kernel. I used kernelcheck to do this. very easy, just takes ages to compile.

---

### Post by ron-toro on 2010-03-16
@daimaru

You were a life saver for my system running 8.04. Last week I had a HDD crash and figured I would get with the program and upgrade. 

I made the dsdt modifications that you outlined, and seem to be experiencing the same issue with initramfs not applying the changes with no gain.

GPU temps running 115-125 C

I've read through some of your notes about creating a custom kernel for this, and I'm asking myself if its worth it.  

If I customize the kernel, I assume I will have to customize every new kernel release... which I'd rather not have to worry about.

Are there any long term solutions, other then getting rid of the laptop?

Toshiba Satellite P105-S9337
Pheonix bios version 4.80

Release 9.10 (karmic)
Kernel Linux 2.6.31-20-generic

NVIDIA Driver Version: 185.18.36

GeForce Go 7900 GS

> **daimaru said:**
> try compiling the dsdt stuff into a custom kernel. I used kernelcheck to do this. very easy, just takes ages to compile.

---

### Post by ron-toro on 2010-03-16
Well after screwing with this for the last 3 days, it works.
I didn't do anything different. It just started working. 

The following were unsuccessful:
-altered the dsdt and tried to use initramfs
[INDENT]dsdt changes didn't stick after reboot - still running hot[/INDENT]
-recompiled the kernel with the new dsdt file
[INDENT]It worked - GPU running cool... but issues with dpkg[/INDENT]


I had reinstalled 9.10 half a dozen times with no difference(still hot). Reinstalled after screwing with the kernel, suddenly works???????
[COLOR="Navy"]Has to be the BIOS. I did all of my testing on a different hard drive, but when I put my operational hard drive back in, it still works.[/COLOR] 
I flashed my BIOS to 4.8 a while ago, so I'm not sure what the difference is now. 
Was at ~120 C now running ~75 C.

---

### Post by daimaru on 2010-03-18
it started working for me with combination of bios update and ubuntu 9.10. Before I did bios update my laptop was running hot too. It seems though that after bios update you have to reinstall ubuntu. At least mine was still running hot after bios update with 9.10 installed. Then I reinstalled (after that custom kernel stuff) and everything worked out of the box. So I am guessing its the combination of updating bios first then installing ubuntu 9.10. Hope I won't need to bother with this again when next ubuntu version comes out.

---

### Post by ron-toro on 2010-03-19
daimaru,
I had thought that too but several of my installs were after the bios flash. All but the last still had the over heat issue. 

Let's hope this is the last time we need to mess with this.

---

### Post by lucag on 2010-03-24
> **ron-toro said:**
> daimaru,
I had thought that too but several of my installs were after the bios flash. All but the last still had the over heat issue. 

Let's hope this is the last time we need to mess with this.

I confirm that reinstalling the bios (4.8 version) and then reinstalling Ubuntu 9.10, fixed the problem, or at least in the last two days the problem didn't show up again. My computer is running cool as it should (40° to 54°).

 My impression is that Ubuntu 9.10 is working but if, just after the bios update, you first run an older ubuntu release or a patched 9.10 release, then something in the bios changes and the overheating appear. It is like if the bios is screwed up by something.  I had to reinstall the bios and I discovered that Ubuntu was working only by chance, just because inserting an SD card in the slot corrupted the video memory and freezed my notebook with the only way out to reinstall the bios. But this is another thread which is not for this forum since it has to do with win 7 that I was running at that moment. 

I'm not (hopefully) going to experiment any more on this.

---

### Post by krantix on 2010-03-24
I noticed that if I boot Windows, login and then restart into Ubuntu (9.10) all my overheating problems disappear. 

I've also recompiled a kernel with the DSDT patch, but the system is working better with the regular kernel and no DSDT patch.

If I remove the battery from the laptop and just start Ubuntu, overheating is there again, so I always have to boot once into Windows to get the system work!

---

### Post by ron-toro on 2010-05-08
Over heat is back w/ kernel 2.6.31-21 and w/ 10.4 clean install.

---

### Post by ron-toro on 2010-05-08
I attempted this fix with 10.4. Still running hot.

---

### Post by daimaru on 2010-05-16
> **ron-toro said:**
> I attempted this fix with 10.4. Still running hot.
Hi ron-toro

i just checked my laptop. with 10.04 clean install (x86_64) here are the results:

kernel 2.6.32-21-generic
full cpu and gpu load --> glxgears running and both my cpus @ ~95% 
Temperature rises to 90° and stays there. 

after turning off glxgears it took about 3 minutes to reach 70 after 10 minutes i checked again and my gpu temperature was at 64°. It seems to stay around 60°-64° when not using any graphics intensive application.

then i updated to new kernel 2.6.32-22-generic
same results. If i just boot up my laptop and leave it running (doing nothing) it runs at 60° under load it goes up to 88°. But it never goes higher then that. 60° and 90° might be high, but I can sort of live with it as long as i don't get the old 125° stuff.

---

### Post by y_lo on 2010-05-28
> **ron-toro said:**
> I attempted this fix with 10.4. Still running hot.

See hereunder for a working solution on a p100, that is supposed to be very close from p105 hardware:
[https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/484875](https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/484875)

A perl script to be called for test... and if OK, to be placed somewhere in init scripts.

---

### Post by Sacob on 2010-10-17
my toshiba has this problem again. I'm using ubuntu 4.10 and it happened a few days. happened to anyone else?

---

