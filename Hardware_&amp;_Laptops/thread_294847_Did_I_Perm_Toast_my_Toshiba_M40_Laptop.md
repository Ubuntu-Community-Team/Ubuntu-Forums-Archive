---
title: "Did I Perm Toast my Toshiba M40 Laptop??"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by kwandar on 2006-11-07
Help!!

Okay, I had Ubuntu (6.06 I believe) installed and partioned in my Toshiba M40 (M45 in US) laptop.  Then I stupidly decided to increase the space Windows required in its partition as it was running short on space, and used Parition Magic.

The result is that when I turn on my computer I get Grub 1.5 Error #17 and it stops.  

Okay I figure, just run the rescue DVD. Changed the bios boot order for CD-Rom first.  But ... I still get the same error.  I tried Ubuntu disk - same problem.  For some reason Grub 1.5 and freezing with Error #17 is still coming up, and I don't understand why when booting from CD?!

The only thing that works is the "instant on" Express Media Player, but that has no ability to boot disks.:( 

I'm at a loss as to how to fix/reformat this laptop if it won't boot the CD, and the bios seems to be very limited, so there aren't a lot of options?  Please help - hate to think this laptop is toast :(

---

### Post by ssalman on 2006-11-07
You may have corrupted one (or both) of your partitions, but most likely you have corrupted your MBR. from the [grub ]("http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors")site

> 17 : Cannot mount selected partition; This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.your first step is to restore grub and then see if further work is needed on your partitions, with good luck you won't need any :)

follow [these ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")instructions. and post back.

---

### Post by ssalman on 2006-11-07
Oh ya, forgot, your HD-installed grub does not control your live CD boot, so if you are still getting the same error, it means that you are not booting off the CD, and still using your HD. for all it cares, you can take off your HD from the PC and the Live CD should be able to boot with no problems. good luck:)

---

### Post by kwandar on 2006-11-07
Well, that's what I thought too.  I definately have it set for CD-rom though?  I'm wondering if its some special whacky bios lockdown feature from Toshiba?  Must be someway to bypass it if there is, but I have no idea.

If I could get to boot a disk I'd be fine, but I can't get there :???: Hell - I'll reformat the whole thing and be happy, but I can't do that?

Is there something with the Toshiba bios that keeps going back to the HD irrespective of where you tell it to boot from?  Only other thing I can think of - as you mentioned, is trying to open it up (yikes) and disconnect HD and try it :(

---

### Post by ssalman on 2006-11-07
> Only other thing I can think of - as you mentioned, is trying to open it up (yikes) and disconnect HD and try it :(

You don't need to open it up to disconnect the HD, there is a special external bay for HD in laptops (with only one screw in most laptops)... BUT if you DONT know what you are doing, don't do it now, I don't want you to toast your laptop for real...up to now I think it's a software issue, let not make it a hardware one ;)

try with the BIOS, it has to be it.

---

### Post by phersotty on 2006-11-07
> **ssalman said:**
> You don't need to open it up to disconnect the HD, there is a special external bay for HD in laptops (with only one screw in most laptops)... BUT if you DONT know what you are doing, don't do it now, I don't want you to toast your laptop for real...up to now I think it's a software issue, let not make it a hardware one ;)

try with the BIOS, it has to be it.

Disclaimer: I don't know if this will work.

Try taking out the battery for a few minutes.  Put the battery back in and see if it will boot from CD now.

---

### Post by kwandar on 2006-11-07
Well, I've tried everything to make it boot a CD.  All I can think is that somehow the Toshiba bios is dumbed down, so when you boot from CD, it still access the HD and the MBR to bring up Grub.

Its bizarre.  I've tried everything to get it to boot a disk, to no avail.  I'm going to try one more thing tonight, and if that isn't it, I'm looking for that one screw - its already qualifying as a boat anchor! :)

Thanks - if you have any other ideas, please keep them coming.

---

### Post by kwandar on 2006-11-07
> **phersotty said:**
> Disclaimer: I don't know if this will work.

Try taking out the battery for a few minutes.  Put the battery back in and see if it will boot from CD now.

I'll give it a shot tonight.  Not sure why that should matter, but there aren't a lot of alternatives, and that's a simple one.  Thanks!

---

### Post by bigken on 2006-11-07
I have toshiba and to boot from the cdrom you either press F1 or F2 to select your boot option failing all else you may need to pull the cmos battery ;)


pulling the hdd will make no difference

---

### Post by kwandar on 2006-11-07
> **bigken said:**
> I have toshiba and to boot from the cdrom you either press F1 or F2 to select your boot option failing all else you may need to pull the cmos battery ;)


pulling the hdd will make no difference

But presumably its finding Grub from the Hard Drive?  So, where the hell is the CMOS battery.  Screwdriver time if I try that, right? :)

---

### Post by Dale61 on 2006-11-08
I'm also a Toshiba user, and I thought I had created a boat anchor.

After trying all options to get the modem to work (still don't have internet access), I attempted to re-install the factory install of Windoze.  All went well until time to reboot, and faced the same error #17 as you encountered.

I eventually reverted to a desktop version of Windoze, and I was prompted to repair the MBR.  As I had nothing to lose, I did so, and once installation was complete, I had my laptop back with an XP install.

As this was a desktop version, I had no sound / modem, etc, so again attempted to re-install from the factory installation CD's.  Error, error, error.  Could read the CD's but couldn't do anything with them.

With Ubuntu, at least I had sound, so went back to installing 6.06, got the sound to work, but still no modem, and thus, no internet connection.  Attempted to network laptop to my desktop, but all this did was lock up my (dial-up modem), so gave up.

I packed up the laptop about 4 weeks ago and didn't even bother with it until today, when I decided to take it into a pc repair shop and see if they can get any sense out of it.  I'm not expecting to see it for a couple of days, and when I do, I'm hoping it is internet ready.

BTW, with all the 'help' I received from these forums, can anyone explain to me how I download something if I don't have internet access?  Nope, didn't think so!

---

### Post by bigken on 2006-11-08
> **kwandar said:**
> But presumably its finding Grub from the Hard Drive?  So, where the hell is the CMOS battery.  Screwdriver time if I try that, right? :)

Have you tired  pressing c when you boot this will make it boot from cdrom (read your manual) download it from [here ;)]("http://uk.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/download_drivers_bios.jsp?service=UK")

---

### Post by Dale61 on 2006-11-08
How to restore Grub to your MBR using the Ubuntu 6.06 live cd.

[Read this]("http://www.arsgeek.com/?p=655#more-655")

---

### Post by bigken on 2006-11-08
> **Dale61 said:**
> How to restore Grub to your MBR using the Ubuntu 6.06 live cd.

[Read this]("http://www.arsgeek.com/?p=655#more-655")


Dale his trouble is that he cant boot from a cd

---

### Post by Dale61 on 2006-11-08
When I had the same problem, I found that persistance paid off as it took about 8-9 attempts of pressing F8 (I think as I currently don't have my laptop in my possession) during POST to eventually get my laptop to boot from the live cd.

---

### Post by kwandar on 2006-11-26
> **Dale61 said:**
> I'm also a Toshiba user, and I thought I had created a boat anchor.

After trying all options to get the modem to work (still don't have internet access), I attempted to re-install the factory install of Windoze.  All went well until time to reboot, and faced the same error #17 as you encountered.

I eventually reverted to a desktop version of Windoze, and I was prompted to repair the MBR.  As I had nothing to lose, I did so, and once installation was complete, I had my laptop back with an XP install.

As this was a desktop version, I had no sound / modem, etc, so again attempted to re-install from the factory installation CD's.  Error, error, error.  Could read the CD's but couldn't do anything with them.

With Ubuntu, at least I had sound, so went back to installing 6.06, got the sound to work, but still no modem, and thus, no internet connection.  Attempted to network laptop to my desktop, but all this did was lock up my (dial-up modem), so gave up.

I packed up the laptop about 4 weeks ago and didn't even bother with it until today, when I decided to take it into a pc repair shop and see if they can get any sense out of it.  I'm not expecting to see it for a couple of days, and when I do, I'm hoping it is internet ready.

BTW, with all the 'help' I received from these forums, can anyone explain to me how I download something if I don't have internet access?  Nope, didn't think so!

Sorry for taking so long to get back.  I ended up taking it to a repair shop and they reinstalled windows, but not the Toshiba disk I gave them and it has "27 days left for activation" now.  So its going back again.  I think they did exactly what you did but I still don't know how they got it to boot the disk? and I want the original recovery DVD disk to install.

I'm thinking a low level format might fix things, but I'm a bit worried and don't want to double the repair fees.

---

### Post by kwandar on 2006-11-26
> **bigken said:**
> Have you tired  pressing c when you boot this will make it boot from cdrom (read your manual) download it from [here ;)]("http://uk.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/download_drivers_bios.jsp?service=UK")

Uhm yes - thank you.  I've even set the bios preferences that way.  Doesn't matter.  Only wants the hard drive.

Even now that I took it for repair, it will not boot the Toshiba Recovery DVD, irrespective of pressing C, F, etc.

---

