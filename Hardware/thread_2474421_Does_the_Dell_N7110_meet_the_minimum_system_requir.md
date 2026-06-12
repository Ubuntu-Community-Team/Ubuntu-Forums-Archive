---
title: "Does the Dell N7110 meet the minimum system requirements for Ubuntu 18.04?"
date: 2022-04-28
forum: Hardware
---

### Post by John_Patrick_Mason on 2022-04-28
I have a [Dell Inspiron]("https://laptoping.com/dell-inspiron-17r-n7110-review.html") 17R N7110 with a 64-bit [Intel Core i3-2310M]("https://ark.intel.com/content/www/us/en/ark/products/52220/intel-core-i32310m-processor-3m-cache-2-10-ghz.html") CPU @ 2.10GHz × 4 with Intel HD 3000 integrated graphics with 4GB of system RAM and a 500GB hard drive.

According to [this]("https://askubuntu.com/questions/333795/what-are-the-system-requirements-for-each-flavour-of-ubuntu-desktop")  Ask Ubuntu source, my laptop meets the recommended minimum hardware  requirements for CPU type, CPU clock speed, system RAM, and disk space.  What I am less sure about is the requirement for a GPU capable of 3D  acceleration with at least 256 MB (of GPU memory?). Like I said, my  particular laptop configuration came with a CPU with integrated  graphics, but it did not come with a dedicated graphics card. I'm  assuming the 256MB number is in reference to GPU memory, correct?

Also,  I'm not sure what the VGA requirement for a VGA capable of 1024 x 768  screen resolution is supposed to mean. VGA is a connector that has  largely been replaced by the HDMI standard, so is this if I want to  connect my laptop to a secondary monitor or a projector?

Anyway, the display has a resolution of 1600 by 900 pixels.

So,  my next question is, is my laptop capable of running Ubuntu 18.04 LTS?  The reason I'm mentioning Ubuntu 18.04 rather than the newer Ubuntu  22.04 LTS version is because I tried to boot from a USB stick with Ubuntu 22.04 and the  system wouldn't even boot.

What about Ubuntu Mate 18.04/22.04 LTS?

If the answer is no to either, then what about Lubuntu 18.04/22.04?


Your help is greatly appreciated.

---

### Post by Yellow Pasque on 2022-04-29
The integrated GPU is fine. It uses the system RAM for GPU memory and will dynamically allocate however much it needs.

> Also, I'm not sure what the VGA requirement for a VGA capable of 1024 x 768 screen resolution is supposed to mean. 

Yeah, it's bad phrasing. The bottom line is that they recommend a display capable of 1024x768, so yours is fine.

Really, the system should run Ubuntu 22.04. I'd recommend trying Xubuntu or Lubuntu 22.04

---

### Post by John_Patrick_Mason on 2022-06-04
> **Yellow Pasque said:**
> Really, the system should run Ubuntu 22.04. I'd recommend trying Xubuntu or Lubuntu 22.04

Sorry for reposting on an old thread, I just wanted to keep the thread open in case I encountered any issues after upgrading to a new OS version. I ended up installing Ubuntu 18.04 LTS after stumbling upon an article by [ZDNet]("https://www.zdnet.com/article/mark-shuttleworth-reveals-ubuntu-18-04-will-get-a-10-year-support-lifespan/") on how Canonical plans to extend support until 2028 vs. Ubuntu 20.04 LTS, which will 'only' be supported until 2025. I would have considered installing Ubuntu 22.04 LTS, but, unfortunately, I wasn't able to even boot from it after creating a bootable USB flash drive, so I opted for Ubuntu 18.04, instead.

However, I've been experiencing a couple of annoying bugs which may be hardware-related, perhaps related to the relatively low RAM. More specifically, after I log in to my account, though it doesn't happen every time, if I let the screen timeout and another user then wants to log in by clicking on "Log in as another user," the machine won't allow to switch users to allow the other user to input his password, and the computer will go back to my user account and ask for my password again. The only thing that can fix the issue is if I enter again my password for my account and then click on "Log Out." If I, instead, click on "Switch User," when I'm logged in, the other user will experience the same issue again. When I experience the issue, I'm basically stuck in a loop on my account, unless if I decide to log out, which I don't always want to do.

I do have plans to upgrade to 8GB of RAM from 4GB, which is the suggested minimum amount of RAM needed to run Ubuntu 18.04.

Do you think this issue that I've been experiencing could be RAM-related?

---

### Post by guiverc on 2022-06-04
I'll add my 2c worth.

Rather than use Ask Ubuntu's page (*fyi: I do see my name many times in the comments on that page though*), personally I'd stick to the official docs on minimum specifications, ie. 

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Also be aware that whilst [Ubuntu 18.04 LTS]("https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/") has 5 years of *standard support*, that includes only Ubuntu Desktop, Ubuntu Server, Ubuntu Cloud, and Ubuntu Base and not *flavors* which you'll note aren't mentioned in the link I provided, as the came with 3 years which had already ended thus didn't provide any updated ISO for 18.04.

Also don't forget ESM (*extended support*) may involved changes, eg. Ubuntu 16.04 LTS completed it's five years of *standard support* in April-2019, and now many desktop packages that came with the system are *unsupported *as per the documentation (*five years*) with further support offered via users exchanging them to *snap* packages. What happens with 18.04 LTS when it *transitions* from *end-of-standard-support* to *extended* or ESM support we can only guess at, but looking at the prior 16.04 release ([see]("https://wiki.ubuntu.com/SecurityTeam/ESM/16.04") etc) may present a pretty good clue.

If your system failed to boot 22.04 LTS, I'd firstly return to basics & did you verify the ISO prior to write to media? and then validate the write to media using another box?  In my experience it's the write to thumb-drive media (*cheap consumable media*) that is most risky, and Ubuntu 20.10 & later involves some changes which mean some older software needed to be updated before it could actually write later ISOs (*media failing to start being the clue that the ISO writing software was outdated*). Also some media can be *slow to boot* & thus you need to be patient (*firmware bugs cause delays of 9-12 mins*).

You asked if your machine doesn't provide dedicated RAM; then normal RAM is used instead, ie. you should really have more RAM to meet the minimum *specs* as your box is using main RAM to substitute for lack of *dedicated video *RAM*. *FYI:  The main effect with lack of RAM is a *slow* machine, ie. it may still technically run perfectly, but the experience maybe better talked as of *slow walking* rather than *running*.  eg. I've used the following machine in QA-testing all releases up to and including 22.04 LTS

- lenovo thinkpad sl510 (c2d-t6570, 2gb ram, i915)

No dedicated gpu RAM & minimal RAM exists; but for Ubuntu 17.10 & later desktop the minimum recommended RAM is 4GB + video RAM (256MB) thus it's equivalent of 4.25GB of RAM which the box fails to meet.  The box consequently has *lighter* flavor(s) installed.

I can't speak to your last question though sorry.

FYI:  QA=*Quality Assurance*

---

### Post by John_Patrick_Mason on 2022-06-05
[QUOTE=guiverc]If your system failed to boot 22.04 LTS, I'd firstly  return to basics  & did you verify the ISO prior to write to media?  and then validate  the write to media using another box?  In my  experience it's the write  to thumb-drive media (*cheap consumable media*)  that is most risky,  and Ubuntu 20.10 & later involves some changes  which mean some  older software needed to be updated before it could  actually write later  ISOs (*media failing to start being the clue that the ISO writing software was outdated*). Also some media can be *slow to boot* & thus you need to be patient (*firmware bugs cause delays of 9-12 mins*).[/QUOTE]

Now  this is interesting. I've had trouble in the past with unbootable USB  flash drives, which led me to throw my hands in the air and give up. The  first time was when I wanted to try a privacy-focused distro which  failed to boot. The second time was when I wanted to try Ubuntu MATE  because it still had that classic Gnome 2 look, and also because I never  really liked Unity as a desktop environment, even though Unity was the  only DE I had ever tried.

[QUOTE=guiverc]did you verify the ISO prior to write to media?[/QUOTE]

Yes.  I always do. I always check ISOs for integrity by doing an sha256sum  and checking the resulting hash against the hash on ubuntu.com before  burning the ISO to the USB flash drive.

[QUOTE=guiverc]and then validate  the write to media using another box?[/QUOTE]

Assuming  I understand your question, I no longer have another machine to test  whether it might be an issue with the USB flash drive itself, but I do  know that after the bootable USB thumb drive with Ubuntu 22.04 failed to  boot, I reformatted the USB stick with Ubuntu 18.04, and that worked on  the first try.

However, I'm not sure if I understand the following sentence when you write:

  [QUOTE=guiverc]In my experience it's the write  to thumb-drive media (*cheap consumable media*)  that is most risky,  and Ubuntu 20.10 & later involves some changes  which mean some  older software needed to be updated before it could  actually write later  ISOs (*media failing to start being the clue that the ISO writing software was outdated*).[/QUOTE]

When  you are referring to the write-to thumb-drive media, or, as you also  call it, "cheap consumable media," are you referring to the USB flash  drive itself, or to the USB port on the computer?

[QUOTE=guiverc]Also some media can be *slow to boot* & thus you need to be patient (*firmware bugs cause delays of 9-12 mins*).[/QUOTE]

Shoot.  I didn't even consider this issue. But, if I remember correctly, when I  created the bootable USB flash drive with Ubuntu 22.04, the computer  went right to the distro that was already installed on the hard drive,  so I don't think it was an issue caused by buggy firmware on the USB  flash drive.

---

### Post by guiverc on 2022-06-05
> **John_Patrick_Mason said:**
> 
When  you are referring to the write-to thumb-drive media, or, as you also  call it, "cheap consumable media," are you referring to the USB flash  drive itself, or to the USB port on the computer?

Shoot.  I didn't even consider this issue. But, if I remember correctly, when I  created the bootable USB flash drive with Ubuntu 22.04, the computer  went right to the distro that was already installed on the hard drive,  so I don't think it was an issue caused by buggy firmware on the USB  flash drive.

> cheap consumable media

I mean the USB flash-drives..    I find with Sandisk brand, about 5-8% of my writes of ISO files to thumb-drive are faulty, and require a re-write. With other [*cheaper*] brands the failure rate is actually higher. For many users that probably won't be that much of a problem, but as I write quite a number rather regularly (*the count of ISOs written today to thumb-drive for me is 3*) I'm very aware of it.

As I'm involved with QA (*Quality Assurance*) I need to rule out issues with media (*inc. bad writes*) thus if it fails on one box; I try booting it on another *like* box (*even if not identical, as close as I can*) to see if it boots there, then boot in a very different machine... if it fails to boot on all - I assume it's a bad write or faulty media & return to the ISO validation & write of ISO to thumb-drive media again....

> the computer  went right to the distro that was already installed on the hard drive

I was doing some testing today related to a couple of different issues, where firstly an ISO written to thumb-drive failed to boot, and the system quickly switched to booting the OS on the internal hard drive... For some boxes that is a sign that the *media* was invalid (*according to its firmware** including the HP box I was testing on*) and it thus decided to ignore it & use the next bootable device (*internal drive*), on others I have it ask me what to do, and others it just throws up an error & asks me to press a key to retry or reboot.  It can also be I didn't press a key fast enough on some boxes (*I have some boxes which are painful to boot external media intentionally as a means of claiming to improve security*). The thumb-drive in my case (today) put in another different box would have booted straight up, so behavior is rather box specific (*the firmware in the box decides what occurs*).  In my case I re-wrote the ISO in a different way & the box booted the same ISO correctly.

The [*slow booting* bug]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1922342") is a firmware issue that means the box just sits there for more than 10 minutes showing nothing, where most people assume it's not booted & didn't work... In fact in the bug report I linked the original poster's description was it failed to boot, and it was only after getting the user to wait ~15 minutes the issue was detected *slow booting* and not failure to boot.  Your description as I tried to express in the last paragraph doesn't fit slow to boot but problems with media according to your box.

If you wrote the ISO to media (USB *thumb-drive*) on a 22.04 box, the chances of older software being an issue is *negligible*.   If you used software that *clones* the ISO to thumb-drive the chances of error are *greatly *reduced too (*bad ISO you've ruled out, though more likely in my experience bad write to ISO the most common failure*).  However some software  re-organizes the ISO as it writes to media (*to provide extra features, eg. persistence etc*) which can create the failure to boot as you describe (*it's what caused [my failure to boot on specific HP boxes]("https://ubuntuforums.org/showthread.php?t=1958073&page=117").. but the failure to boot in my case was expected; as the subsequent write with different option was also supposed to work which it did - the purpose of my testing*). 

**Summary**.

If I was in your shoes, I'd verify the write of ISO to your media as I'd normally do [using other boxes]("https://askubuntu.com/questions/1311183/do-i-need-to-check-the-integrity-of-a-ubuntu-install/1311209#1311209")... Easy for me, given I've ~25 boxes I use in my QA-testing.. alas that's an option you don't have available anyway.

---

### Post by Yellow Pasque on 2022-06-05
Is there any chance you can get to a terminal in situations where it doesn't boot? (ctrl + alt + F1) or (ctrl + alt + F2)
Then you can look at things like:
```
free -m
dmesg
journalctl -b
```

---

### Post by Yellow Pasque on 2022-06-05
> Do you think this issue that I've been experiencing could be RAM-related? 
I doubt it. It seems like a bug with gdm. But again, you can drop to a terminal and look at:
```
free -m
```
to see the memory situation.

EDIT: Sorry for double post. I have scattered thoughts..

---

### Post by John_Patrick_Mason on 2022-06-05
> **guiverc]As I'm involved with QA (*Quality Assurance*) I need to rule out issues with media (*inc. bad writes*) thus if it fails on one box said:**
> 

What  qualifies as a "like box" when testing an unbootable USB flash drive  when doing QA? Do you use a machine with the same OS version? Or do you  use a machine with the same chipset/motherboard? In other words, what  I'm asking is, how do you define what makes a machine a "like box" if I  were to one day do QA myself?

[QUOTE=guiverc]I was doing some testing today related to a couple of different issues,  where firstly an ISO written to thumb-drive failed to boot, and the  system quickly switched to booting the OS on the internal hard drive...  For some boxes that is a sign that the *media* was invalid (*according to its firmware** including the HP box I was testing on*) and it thus decided to ignore it & use the next bootable device (*internal drive*)

When  you say that an unbootable USB flash drive is a sign that the media is  invalid according to its firmware, including the HP box, what type of  firmware is at fault in this case? The firmware on the unbootable USB  flash drive, or the UEFI/BIOS firmware on the machine's motherboard?

[QUOTE=guiverc]The thumb-drive in my case (today) put in another different box would  have booted straight up, so behavior is rather box specific (*the firmware in the box decides what occurs*).[/QUOTE]

When you say firmware, you mean the BIOS/UEFI firmware, correct?

[QUOTE=guiverc]In my case I re-wrote the ISO in a different way & the box booted the same ISO correctly.[/QUOTE]

How  did you go about doing this? Did you use the GUI tool Startup Disk  Creator in a different way? Or did you go with command-line utilities?  I'm only asking because, like I've said before, I've had issues in the  past with unbootable USB flash drives, and I'm wondering if using a  different set of tools to create the bootable USB flash drive (other  than Startup Disk Creator), or using the tools that I typically use in a  different way, would help.

[QUOTE=guiverc]If you used software that *clones* the ISO to thumb-drive the chances of error are *greatly *reduced too[/QUOTE]

When you say *clone*  the ISO to thumb drive, are you referring to something like the dd  command, AKA "disk destroyer"? How can I clone an ISO to USB in order to  reduce the chances of error?

[QUOTE=Yellow Pasque]Is there any chance you can get to a terminal in situations where it doesn't boot? (ctrl + alt + F1) or (ctrl + alt + F2)[/QUOTE]

I suppose I can try again. However, I'm going to have to download the Ubuntu 22.04 ISO again, since I deleted it. Hopefully, the ISO hasn't changed since I last downloaded it. That being said, I do remember doing an sha256sum on the ISO, as I always do, so if the ISO hasn't changed, I should be able to replicate the issue.

[QUOTE=Yellow Pasque]I doubt it. It seems like a bug with gdm.[/QUOTE]

That was actually my first thought, but, then, I began to second guess myself and thought it might have to do with the low RAM, which I plan on upgrading. Though I much prefer Gnome 3 over Unity, this release of Ubuntu (Ubuntu 18.04) has been the buggiest release of Ubuntu I have ever dealt with. I've also been getting these error pop-ups, but, unfortunately, when I want to send the diagnostic data back to Canonical, the error pop-up won't allow me to do so (I have it set to manual reporting, instead of automatic). Should I ask to have a bug report filed on my behalf?

The last, and final (albeit minor), issue I've been having is when I let the screen time-out and I have to reenter my login password, right after I've successfully reentered my password, the screen will then turn black and stay that way until I move the mouse or reach for the touchpad, instead of waking up and automatically going back to where I was.

---

### Post by guiverc on 2022-06-06
> **John_Patrick_Mason said:**
> In other words, what  I'm asking is, how do you define what makes a machine a "like box" if I  were to one day do QA myself?

The following boxes I'd consider *alike*

- dell [optiplex] 745 (c2d-6600, 6gb, amd/ati radeon rv516/x1300/x1550)
- dell [optiplex] 755 (c2d-e6850, 5gb, amd/ati radeon rv516/x1300/x1550)
- dell [optiplex] 755 (c2d-e8300, 8gb, amd/ati radeon rv610/radeon hd2400 pro/xt)

as they are rather similar.   I may also include some other later models
- dell [optiplex] 780 (c2q-q9400, 8gb, amd/ati cedar radeon hd 5000/6000/7350/8350)
- dell [optiplex] 960 (c2q-q9400, 8gb, amd/ati cedar radeon hd 5000/6000/7350/8350)

or for the HP box I mentioned; it and another I consider a *like* box are
- hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)
- hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)

They are rather similar boxes; not really in looks, but in terms of motherboard, firmware (*code stored on a chip on the motherboard*) etc.   The dell 960 though has later *firmware* even though *spec* wise it's identical to the 780, thus the 780 & 960 are identical only if the *BIOS* configuration matches.

A very different box maybe the following
- sony vaio svp112a1cw (i5-9400u, 4gb, intel haswell-ULT)
- samsung 700t1c-p10aat (i5-3317u, 4gb, 3rd gen.core.intel.graphics.4000)

primarily as those two are uEFI or Secure-uEFI only; thus boot very different to the older boxes I mentioned. 

If I wanted a *like* box to the HP dc7700; I consider the dc7900 avery like box, I'd likely use the older 755 as another *like* box (though it has very different firmware code; so when dc7700 refuses to boot something - I expect the dc7900 to boot/fail in the identical way - but dell 755s may give different results.  The sony/samsung in my example are completely different boxes as aren't *legacy/BIOS/CSM *in booting but use uEFI.

Note with the *like* box in my example I'm thinking of **BOOTING** only, and sure not graphics for example... The two HP dc7700 & dc7900 are extremely different when it comes to say graphics.  If it was graphics, the HP dc7700 would be like a HP 8200 that also uses nVIDIA.... etc


> **John_Patrick_Mason said:**
> 
When  you say that an unbootable USB flash drive is a sign that the media is  invalid according to its firmware, including the HP box, what type of  firmware is at fault in this case? The firmware on the unbootable USB  flash drive, or the UEFI/BIOS firmware on the machine's motherboard?

When you say firmware, you mean the BIOS/UEFI firmware, correct?

Yes, the old HP dc7700 & HP dc7900 contain firmware which contains standards compliant errors & doesn't correctly follow the BIOS booting instructions.  They were sold with windows XP & booted the old XP media fine, but cannot boot later uEFI compliant media due to the errors; but they were sold before later versions of windows existed so no-one cared. 

 Ubuntu & other GNU/Linux has to deal with booting on modern standards compliant boxes; plus old legacy boxes..  Ubuntu carried code that specially dealt with the firmware (*on chips*) on> **John_Patrick_Mason said:**
>  these old HP boxes so they could boot *modern* OSes, however of late it's been discovered the extra *legacy* code carried so these old boxes from ~2005 can boot - is creating problems for newer machines using uEFI.  My actual testing is to try and work out what will boot on these old boxes; but that will also boot on the more modern boxes (*owned by other testers** and reported by bug reports*). 

I maybe complicated things for you, for which I'm sorry.


[QUOTE=John_Patrick_Mason;14098922]
How  did you go about doing this? Did you use the GUI tool Startup Disk  Creator in a different way? Or did you go with command-line utilities?  I'm only asking because, like I've said before, I've had issues in the  past with unbootable USB flash drives, and I'm wondering if using a  different set of tools to create the bootable USB flash drive (other  than Startup Disk Creator), or using the tools that I typically use in a  different way, would help.


I provided a link in my prior message to a [report written to another user here]("https://ubuntuforums.org/showthread.php?t=1958073&page=117") on some of that testing.  I used `[mkusb]("https://help.ubuntu.com/community/mkusb")` in that testing, but in most cases I'm just following instructions & reporting back issues.   The post I linked relates only to `mkusb` as that was what I was actually testing in that session, but that was based on prior testing which was done using various commands talked about in numerous bug reports.

Myself, I use `mkusb` in almost all cases; though if a machine doesn't have `mkusb` installed I usually use `dd`, though do use other tools too just to confirm I get the same results regardless of which *supported* *method of writing the ISO* is used or my usual use of mkusb.


> **John_Patrick_Mason said:**
> 
When you say *clone*  the ISO to thumb drive, are you referring to something like the dd  command, AKA "disk destroyer"? How can I clone an ISO to USB in order to  reduce the chances of error?


Yep I am.

Looking up my command history I see this command

```
sudo dd bs=4M oflag=sync status=progress of=/dev/sdb if=/de2900/lubuntu_64/impish-desktop-amd64.iso

```

which may not have been the last time I used it; as most of my commands have spaces in front of them so they aren't recorded in my terminal log (esp.* when it's a routine command where I don't expect issues*).

I tend to use `mkusb` as I overwrote a 2TB data drive, then a 11TB drive array...

---

### Post by sudodus on 2022-06-06
A short explanation: [**mkusb**](https://help.ubuntu.com/community/mkusb) can clone, and that is by far the best method for more than 90 % of the cases, when you want to create a USB boot drive.

- **cloning** - copy 1:1 from the iso file to the target device, robust method, creates live-only drives from Ubuntu family iso files.

- **creating persistent live systems** - in these cases you must do something more complicated than cloning, and mkusb has 3 different methods, that may fit different users and computers

. **[FONT=Courier New]dus-persistent[/FONT]** - the classic mkusb way to make persistent live drives

. **[FONT=Courier New]dus-iso2usb[/FONT]** - new, can be used both to make persistent live drives and live-only drives, can work where other methods fail (even where cloning fails or is very slow in some old computers)

. **[FONT=Courier New]mkusb-plug[/FONT]** - can clone to make live-only drives and 'semi-clone' to make persistent live drives with as little modification as possible of the boot structure from the iso file. 'semi-clone' works with Ubuntu family iso files with version 20.04.x LTS and newer (not with 18.04.x LTS). The name 'plug' is due to the special method to identify the target device (developed by Thomas Schmitt).

[hr][/hr]
All mkusb versions and methods have one feature in common: They **help the user find the correct target device** (and avoid overwriting valuable data on other devices). This was actually the original reason why it was developed, and has still a very high priority.

---

### Post by John_Patrick_Mason on 2022-06-09
Sorry for the late reply, this is still an active thread. Like you, I'm  trying to juggle the daily requirements of life with other things.

[QUOTE=guiverc]However some software  re-organizes the ISO as it writes to media (*to provide extra features, eg. persistence etc*) which can create the failure to boot as you describe[/QUOTE]

Now  that I think of it, I do remember trying to create a persistent drive  for the privacy-focused distro, which failed to boot, after successfully  creating a bootable non-persistent USB flash drive. I'm not sure which  tool I used, probably `dd`, given that I was more familiar with that  command than `mkusb`, at the time.

So, let me make sure I understand everything you wrote. Assuming I'm using a later version of Ubuntu, such as Ubuntu 22.04, and either `dd` or `mkusb`, if I create a bootable USB flash drive and attempt to boot from the drive on box 1, and later on box 2, and booting fails on box 1 *and *box 2, then, in all likelihood, the issue is caused by a bad write, either because I got unlucky because of the 5-8% failure rate of the USB thumb drive or because the software that I used to create the drive reorganized the ISO if I was trying to create, say, a persistent drive, but if booting fails only on box 1 but succeeds on box 2, then, in all likelihood, the BIOS/UEFI firmware on box 1 is just being difficult and I should rewrite the USB thumb drive in a different way?

[QUOTE=guiverc]I tend to use `mkusb` as I overwrote a 2TB data drive, then a 11TB drive array...[/QUOTE]

Stuff happens. I guess that's why it's sometimes called "disk destroyer."

---

### Post by guiverc on 2022-06-09
> **John_Patrick_Mason said:**
> 
So, let me make sure I understand everything you wrote. Assuming I'm using a later version of Ubuntu, such as Ubuntu 22.04, and either `dd` or `mkusb`, if I create a bootable USB flash drive and attempt to boot from the drive on box 1, and later on box 2, and booting fails on box 1 *and *box 2, then, in all likelihood, the issue is caused by a bad write, either because I got unlucky because of the 5-8% failure rate of the USB thumb drive or because the software that I used to create the drive reorganized the ISO if I was trying to create, say, a persistent drive, but if booting fails only on box 1 but succeeds on box 2, then, in all likelihood, the BIOS/UEFI firmware on box 1 is just being difficult and I should rewrite the USB thumb drive in a different way?


Not really. I sort of know my boxes and the firmware in them mostly due to loads of experience booting ISOs written in various cycles of Ubuntu development. 

In understanding ISOs written to media; I'd trust what @sudodus says, given he is a maintainer/developer of `mkusb` thus understands the issues far more thoroughly. Me, I'm really just a QA-tester in this regard and much of my knowledge is based on experience in QA, and I'd trust Sudodus over me.

I've found a ISO written to thumb-drive may fail to boot on another *like* boxes (eg. *if I want to install on a BIOS/legacy/CSM box but it fails to boot; it may fail on other BIOS/legacy/CSM boxes, but successfully boot on uEFI/Secure-uEFI boxes*) but boot successfully on uEFI/Secure-uEFI boxes. Thus I tend to treat
- BIOS/legacy/CSM 
- uEFI
- Secure-uEFI 
rather separately (*and thus if it boots in one box; it'll usually boot in others of the same class*).

With Lubuntu, those three are treated separately in our QA (*Quality Assurance*) testing, as is shown [here]("https://phab.lubuntu.me/w/release-team/testing-checklist/") and [here]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743") as it's a *flavor* I'm heavily involved with. Lubuntu isn't unique though; if we have problems with a specific *type* of box - the next thing we do is confirm Ubuntu is also impacted, then another *flavor* too; as all will be impacted in 99% of cases.  Our testing though in QA ensures all *released* products should boot in all modes if correctly written (eg. *cloned* to USB media), but that's not really an assumption I can make using *dailies* of an *unreleased *product.  If however you're talking about a non-cloning write of ISO to media; I'm tempted to also assume nothing too.  For the non-cloned ISOs written to media; I've found the types I've mentioned tend to act very much in groups (*outside of firmware issues such as some uEFI & even some BIOS/CSM boxes booting very slowly with recent media*;* these unique firmware issues I cannot predict before they occur*).

In summary; if it boots in other boxes of the same *types* I've specified here; I'll feel **more confident **in a successful write, though if it was me, I always jump to terminal & scan the systemd journals to ensure scan of media completed successfully (*if it was older releases like 18.04 there is a menu item that performs this as it wasn't automatic though errors are still pretty easy to detect as squashfs errors*). Failures to boot though don't allow you to scan any logs.  

Please also note: As a boxes *firmware* can be different to other boxes; you cannot really assume anything (*unless you have an exact duplicate make/model that you've checked booted with an OS & noted the firmware was actually identical*); thus it's more ***confidence ***for mewith regards a successful write.

I apologize if I've clouded the issue for you.

---

### Post by John_Patrick_Mason on 2022-06-09
[QUOTE=guiverc]I apologize if I've clouded the issue for you.[/QUOTE]

No need to apologize. At least I now know that, sometimes, when a bootable USB flash drive fails to boot, *it can* be because of the particular BIOS/UEFI firmware on the box, assuming the ISO was written correctly.

---

