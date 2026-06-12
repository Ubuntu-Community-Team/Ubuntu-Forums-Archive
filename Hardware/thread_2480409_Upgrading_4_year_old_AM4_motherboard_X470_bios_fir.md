---
title: "Upgrading 4 year old AM4 motherboard X470 bios firmware to install Ryzen 9 5950X chip"
date: 2022-10-28
forum: Hardware
---

### Post by Drone4four on 2022-10-28
AMD prices for AM4 socket chipsets have come crashing down in recent weeks due to the release of next gen AM5 socket parts. Now is a great time to scoop up some terrific bargains!

I bought my current Ryzen 7 2700 CPU (8C 16T) in October 2018, so a little over 4 years ago. It’s served me well over the years.

Today’s brand new AM5 motherboards (even the entry level ones) cost double what previous gen boards cost. The same is true for DDR5 ram sticks compared to DDR4.

So from my perspective, it makes more sense to take my PC to my local repair shop and have a professional flash the bios on my aged AM4 motherboard and then purchase a high end Ryzen 9 5950X CPU (16C 32T) for a really great price.

Here is the output for the following command:

```

$ inxi -mobo
Machine:
Type: Desktop System: Gigabyte product: X470 AORUS ULTRA GAMING v: N/A
serial: <superuser required>
Mobo: Gigabyte model: X470 AORUS ULTRA GAMING-CF v: x.x
serial: <superuser required> UEFI: American Megatrends v: F2
date: 03/14/2018

```

As you can see in the first line, the version/revision ID is not specified. I ran the same command as superuser and the serial was still redacted. Not sure what that is about.

[Here are the specs for my motherboard on the manufacturer’s website]("https://www.aorus.com/motherboards/X470-AORUS-ULTRA-GAMING-rev-10/Specification").

[Under support, they offer downloads for firmware updates but there is no option for Linux. All it shows is Windows 10/11]("https://www.aorus.com/motherboards/X470-AORUS-ULTRA-GAMING-rev-10/Support") (yuk).

How are Linux users like myself expected to download and install bios firmware updates?

Even if the repair technicians flash the motherboard successfully without Windows, my next question is: What should I expect in terms of stability?

I’m worried that since my X470 board is 4 years old, even with the latest firmware, I could experience frequent or even infrequent crashes which the repair shop technicians won’t be able to test or detect long enough to know for sure. If I discover stability issues after running my hardware over a one or two week period, then that is an expensive $549 mistake forcing me to return to the PC shop to then have to buy a brand new AM4 motherboard, RAM, and CPU.

Having said all of that, based on the knowledge and experience all of you people have with AMD motherboard hardware / firmware updates, what can I expect in terms of reliability and stability on Linux when installing a 5950X CPU into a 4 year old motherboard after flashing the bios?

That’s my main question.

As a side note, to comment further on the purpose for an upgrade: The AMD Ryzen 7 5800X3D is even more affordable and it outperforms the 5950X but primarily in gaming which isn’t relevant to my use case. My use case involves, among other things, many concurrent Chrome and Chromium instances running with hundreds of tabs open in each. I already have plenty of RAM (64 GBs DDR4). So maximum threads would help handle my load rather than fewer threads and more cache.

---

### Post by TheFu on 2022-10-29
I'm with you.  I have a 2600 that I'll likely swap for a 5600G ASAP.  I've missed a few great deals - just this week the 5600G was $119 at Microcenter.  That's my "buy price".

Gigabyte is known for disliking Linux.  They used to be hostile, though it seems they've backed off that to just saying "we don't support Linux".  I remember trying to get any help from them in 2014 and being treated extremely poor.  Stopped buying their stuff then. Sometimes they have a competitive solution, but that prior experience left me with a bad feeling. Fortunately, we have choices for where to spend our money.

The BIOS will have a way to be updated without any OS.  That's what you should use.  Typically, it involves placing a .bin file onto a fat32 flash drive and using the BIOS screens to update.  There are many different BIOS updates on motherboard vendor websites.  Only 1 is needed for the motherboard.  All the GPU and other firmware updates that other OSes use are included in the Linux kernel (eventually), so we don't need to worry about hunting down sound or network chip drivers on Linux 99% of the time.  There's an entire "firmware" tree in the kernel files on your system.

Some MB BIOSes even have a 1-button internet flash update feature.  My Asus B450 boards had that when I bought them, but it was removed for some reason in a later BIOS update. I miss it.  I have 2 Ryzen systems running the exact same BIOS version - one has a 2600 and the other has a 5600G. Both use the same G.Skill 3200Mhz RAM too.

If you can download a file, copy it to a flash drive, reboot your computer, and find the BIOS update page in the current BIOS (usually not hard), and select the file from the flash drive to be uploaded as the new BIOS, you have all the necessary skills.

Flashing the BIOS usually does reset all the settings to factory state, so it is a good idea to get your point-n-shoot/smartphone camera out and take photos of each screen BEFORE flashing. Be certain to scroll down to get the 2nd half of the page.  This way, you can put all the customized settings back under the new BIOS.  Ryzen is picky about RAM and RAM settings.  Pay special attention to the voltages and speed settings.   Also, if you run virtual machines (I do), be certain to know where the setting for that in the BIOS screens are.  That seems to be reset and it isn't called AMD-v for some reason.  I think they call it SVM  in Asus just to make it NOT be the AMD name? IDK.

Some motherboard BIOS have an auto-overclock feature, which will reboot the system 2-4 times seeking the best performing settings that are still stable. This can be useful for the boards with that feature, assuming it works.  I suspect they connect to the internet and pull down the settings from a DB. Again, this feature can be removed, so best to have photos of all the screens.

---

### Post by TheFu on 2022-10-29
> **Drone4four said:**
>  

As a side note, to comment further on the purpose for an upgrade: The AMD Ryzen 7 5800X3D is even more affordable and it outperforms the 5950X but primarily in gaming which isn’t relevant to my use case. My use case involves, among other things, many concurrent Chrome and Chromium instances running with hundreds of tabs open in each. I already have plenty of RAM (64 GBs DDR4). So maximum threads would help handle my load rather than fewer threads and more cache.

Rather than spending hundreds on a system for inefficient use, perhaps working different would make more sense?  

If you are running automatic selenium tests, just accept that you want a fast CPU with plenty of RAM.  That will always be the situation.  You can use virtual frame buffers for those tests to drastically reduce hardware needs, however.

If you are just a lazy home user, setup a wallabag server (mine is in an lxc/lxd container) which is like a read-it-later clone that stores webpages local until I delete them.  These can be used indefinitely, since they don't need internet to work. They are easily found through search or tagging inside wallabag.  Adding a new webpage is easy thanks to a browser addon.  [https://github.com/wallabag](https://github.com/wallabag)   There are iOS and Android apps for your tablet/phone as well.  There's a docker version for the server, which should make the installation easier.   My wallabag server container uses under 1GB of storage and peak memory use is 
```
  Memory usage:
    Memory (current): 434.79MB
    Memory (peak): 624.47MB
```
Just sayin' there are more efficient ways to work, sometimes.  Only you can decide what modes work for you.  I'd be surprised if this wasn't more efficient.  

Browsers are hogs.  I use a sandbox to restrict how much RAM my browser instances can grab to 9G.  The amounts are really crazy these days because the Linux kernel doesn't actually check for out-of-RAM errors when memory is allocated.  A process can ask for 256G of RAM and it will be told "fine", even on a 1GB RAM system.  Until the RAM is actually used, the linux kernel won't know if there is enough or not.  Crazy, right?  Before I put a memory limit on the browsers, they were each grabbing 69GB when my systems only have either 16 or 32G of RAM.  I started limiting at 4G, but the browsers would crash, so I upped the limit to 8G ... they'd crash, but not as often.  At 9G, they don't crash - at least not that I notice.```

PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND   
30405 tf        20   0 4719324 885448 292212 S  13.5  2.7 126:17.33 firefox   
```
That's with about 30 tabs open.  11 are "permanent" - tabs I always have open and pinned for easy use. The others are to be read today. If I can't get to them all, they will be 'bagged' and closed.

---

### Post by Yellow Pasque on 2022-10-29
> As you can see in the first line, the version/revision ID is not specified. I ran the same command as superuser and the serial was still redacted. Not sure what that is about.
You don't want to give the serial number out on the internet. The only thing the serial number should be used for is to return/register the product.

EDIT: As far as running a newer CPU in an older motherboard, you should be just fine if you don't mess around with overclocking. X470 boards were designed to handle AMD's most powerful desktop chips at the time. Later AM4 CPU's are more power efficient at similar frequencies. I upgraded my system with an Aorus B450 mobo from a 2400G to a 5600G with no problem. The Socket AM4 platform was a really good design for those who like to upgrade instead of doing a new build every time.

---

