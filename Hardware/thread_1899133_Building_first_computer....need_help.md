---
title: "Building first computer....need help"
date: 2011-12-22
forum: Hardware
---

### Post by whatthefunk on 2011-12-22
Im building my first pc but am feeling a little overwhelmed...I dont know much about hardware.  I want to build a computer to be used for internet, document editing, videos/music, and occasional gaming.  Im going to run some branch of the Debian family on it (Kubuntu, Mint, or Debian probably).  My budget is around $700.

It seems that choosing a motherboard is the place to start...Im totally lost.  For occasional gaming, is an onboard graphics card going to cut it?  Which is better: Intel or AMD?  What kind of Linux compatibility issues am I going to have?  ASUS motherboards all come with UEFI BIOS...is that going to be a problem?

---

### Post by Jagoly on 2011-12-23
There's no need to be worried, friend. Building a PC can be daunting at first, but go through things one at a time, and you'll be fine.

For CPU's (and their chipsets), the current performance/value leaders are Intel's Sandy Bridge i5's. If you don't want to overclock, then the core i5 2400 is perfect. If you don't mind overclocking (sandy bridge makes this very easy), then spending a bit extra on 2500k will be well rewarded.

UEFI poses absolutely no problem for Operating Systems; it's merely an interface for the bios in most regards. However, I would not recommend an ASUS board for linux compatibility. Most likely they will work fine, but ASUS do not officially support linux on their boards. For best results, go with something from MSI. They have lots of excellent boards in the $100-$200 price range. A Micro ATX board would probably be right for your usage.

For any gaming, do not even attempt to rely on onboard graphics. A $70 nvidia GT 520 will be twice as fast, and have far less compatibility issues (intel graphics do not have compatibility issues with linux, but do not support newer versions of OpenGL, limiting what they can run). 

Although for $130 you can get a GTX 550ti, one step up from a 520, which will allow "serious" gaming. The 550ti is about twice as fast as the 520, because the 520 is designed to be very small and have a low power consumption, eg for HTPCs, where as the 550ti is a "proper" graphics card.

---

### Post by mastablasta on 2011-12-23
what kind of games?
 
For text, internet and watching video/listening to music you can pass with cheapest CPU available...
you can get something for about 400$ to do all those things and more.

---

### Post by Jagoly on 2011-12-23
create the rig that suits your needs, then with any excess budget, future proof it.

---

### Post by whatthefunk on 2011-12-23
Thanks for the replies!

Ok, ASUS is out.  Ive done some more research and yeah, it looks like Id be headed toward massive compatibility problems if I went that way.  What about Gigabyte and ASRock?

So if I go with a micro ATX board and get a smaller case, would the graphics card fit?  I was looking at slim cases, but I couldnt figure out hw the graphics card would get in there.  Or the power supply for that matter...

Speaking of power supplies, what wattage should I go with?  600W?  Is that overkill?

---

### Post by pbpersson on 2011-12-23
I did some Google searches on Ubuntu HCL but did not find many pages that list motherboards and reviews of people who have tried them with Ubuntu.  [This web page]("http://linuxhcl.com/") does list some though.

HCL stands for Hardware Compatibility List

---

### Post by Jack Brown on 2011-12-23
You can actually play a number of current games on integrated video cards from intel.  Saw one guy playing new online first person shooter with an integrated video card.

and lots and lots of old games run well on today's integrated video cards.

you can leave the video card for last.  as an upgrade, when you need it.
as long as you get a motherboard with a video slot.   (most probably pcie x16 slot)

---

### Post by Jagoly on 2011-12-23
for mobos, Gigabyte is the absolute worst for linux support. They specifically state that they DO NOT support linux, and will treat you as such. ASrock is pretty good, not official like MSI, but still good. My server (ubuntu server edition) has an ASrock H67M-ITX. The USB3 did not work in 11.04, but works perfectly in 11.10. This is due to the etron (makes it's usb3 controller) driver being added to the 3.0 kernel.

On a side not, every MSI mobo with usb3 has an NEC controller, which have been supported on linux since they were released. MSI generally doesn't put things in their boards that simply won't work with linux, like other manufacturers do.

PSU is more than anything dependent on your GPU. non OC'd sandy bridge CPU's are very energy efficient. using the integrated graphics, a 250w PSU would suffice. However, upon adding a decent GPU (I still recommend the excellent GTX 550ti from nVidia), you will need a better power supply. I would say a 500-600w PSU would be perfect. If going m-atx, then a moduler PSU would be of more importance.

Avoid slim htpc-style cases. You want a "normal" desktop case, just a bit smaller. I can't give any recommendations, but I'll be looking around for you.

---

### Post by whatthefunk on 2011-12-23
Im looking at the ASRock Z68 Pro3 motherboard.
[http://www.phoronix.com/scan.php?page=article&item=asrock_z68_pro3&num=4](http://www.phoronix.com/scan.php?page=article&item=asrock_z68_pro3&num=4)
Outside of a display problem that can be worked around, and missing support for the integrated graphics card, it looks like it will work alright.

For a harddrive, I was going to go with a Seagate.  Are those good?

---

### Post by Jagoly on 2011-12-23
That looks like a good board. You may also wish know that there is an m-atx variant of this board, with the only notable exclusion be a slightly lower end cpu power system, but that will only affect overclocking.

And one other thing, to those saying that intel's integrated graphics are OK for basic duties and light games: On linux, they are NOT.

Intel's linux driver stack is open source, whilst intel develops the windows driver. This means that there are huge performance differences between windows usage and linux usage. Compare that to nVidia's (and AMD's) proprietary stacks, which are indeed the same for windows and linux, merely packaged differently, will yield identical performance regardless of OS.

My server, which contains an i3-2100t, is by no means slow as a headless server. However, the graphics, when running ubuntu 11.10 desktop (on a HDD, not live cd), are unable to even deliver a fluent unity desktop experience. And playing, as an example, minecraft, it can't even deliver a smooth game (hangs around 15fps) on remotely decent settings. This is at 1280x1024. If you ever use wine to play games, then things are even worse. Wine is designed for a proper GPU, and most things will not work at all with intel.

Read up here for a bit more info: [http://www.phoronix.com/scan.php?page=article&item=intel_hd3000_winbuntu&num=1]("http://www.phoronix.com/scan.php?page=article&item=intel_hd3000_winbuntu&num=1")

I understand that you may not intend to game heavily, it just annoys me when people say that intel's graphics will handle games heavier than tetris. They will way the entire machine down. Build your system with a graphics card; an nVidia GT 520 for $60 will outperform intel's graphics by a minimum of 500%.

PS: I've never bought a Seagate HDD, all of my drives have been Western Digitals. However somehow I've never had a drive fail. I have a maxter 20gb drive in a pentium 3 machine that has seen constant use by multiple people for well over a decade, and it still works fine. Although I'm sure this isn't normal. But I'm sure any recent drive will be fine.

---

### Post by SnickerSnack on 2011-12-23
I recently built a new computer (see below).  These were about the best options I could find on newegg at the time.  In all, I spent about $900, but I used some existing parts: hard drive, keyboard, mouse.  That number also includes the $210 monitor.

I recommend you go with AMD.  They are cheaper and are more than sufficient for what you described.  Intel is better on a performance/dollar basis, but not on a usefulness/dollar basis, for your needs.  I went with AMD largely due to Intel's anti-competitive practices in the past, though.  If you go with AMD, and you want to overclock, then get a black edition phenom II.

If you want an exact number on your power supply, here's a calculator: [http://extreme.outervision.com/psucalculatorlite.jsp](http://extreme.outervision.com/psucalculatorlite.jsp)

It's probably not useful information since you're not looking at gigabyte for the motherboard, but be aware that they don't like to boot from usb.  That's something I discovered after assembling the computer.

For the PSU, I strongly recommend Seasonic.  They cost more, but are well worth it.  The one I have has a surge suppressor in it.  I don't know if that's standard though.

For RAM, you should probably get Kingston or Corsair.  I went with GSkill because there was a sale on their CAS 7 ram.  4GB should be plenty.  I went with 8 because I'm going to run win7 in a vm later.

Some other websites I used to research parts:
[http://www.tomshardware.com/](http://www.tomshardware.com/)
[http://benchmarkreviews.com/index.php](http://benchmarkreviews.com/index.php)
[http://www.guru3d.com/](http://www.guru3d.com/)
[http://www.anandtech.com/](http://www.anandtech.com/)

If you get an after market cooler for the cpu, then you *must* read this: [http://benchmarkreviews.com/index.php?option=com_content&task=view&id=170&Itemid=1](http://benchmarkreviews.com/index.php?option=com_content&task=view&id=170&Itemid=1)

I also highly recommend newegg.com if you're in the US.

---

### Post by kurt18947 on 2011-12-23
> **SnickerSnack said:**
> 
<snip>
It's probably not useful information since you're not looking at gigabyte for the motherboard, but be aware that they don't like to boot from usb.  That's something I discovered after assembling the computer.
<snip>


If your Gigabyte M.B. is like mine, MA785GM-US2H, try formatting the USB drive in Windows then create the LiveUSB.  My M.B. has an Award modular BIOS and apparently the boot module was written by Microsoft.   A USB drive with factory formatting or partitioned and formatted with Gparted then created with Unetbootin would not boot.  The LiveUSB would boot in an older Gigabyte M.B. or ThinkPad. The same USB drive, after being formatted in Windows 7 and created with Unetbootin would boot in the newer Gigabyte M.B.  i was googling around and found this solution.  I don't recall what was  different between a USB with factory format and one formatted by  Windows but there appears to be something.

---

### Post by SnickerSnack on 2011-12-23
> **kurt18947 said:**
> If your Gigabyte M.B. is like mine, MA785GM-US2H, try formatting the USB drive in Windows then create the LiveUSB.  My M.B. has an Award modular BIOS and apparently the boot module was written by Microsoft.   A USB drive with factory formatting or partitioned and formatted with Gparted then created with Unetbootin would not boot.  The LiveUSB would boot in an older Gigabyte M.B. or ThinkPad. The same USB drive, after being formatted in Windows 7 and created with Unetbootin would boot in the newer Gigabyte M.B.  i was googling around and found this solution.  I don't recall what was  different between a USB with factory format and one formatted by  Windows but there appears to be something.

I have a GA-990FXA-UD3, and I think it is one of the newer models.  I'll try formatting in windows when I get access to a windows machine.  I usually make my flash drives fat, so I'll also try just formatting it NTFS (since I can do that now).

Edit: You must have not meant to format it as ntfs, but rather to use windows to format it to fat.  I'll do that when I can.  Thanks.

---

### Post by whatthefunk on 2011-12-24
Alright, heres my build so far:

Motherboard: ASRock Z68 Pro3
CPU: Core i5 2400 3.1 GHZ
Video card: Palit GeForce GTX 550 Ti Sonic
CPU Cooler: Scythe SCMG-3000
CD/DVD: LG GH24NS7
PSU: Kuroutoshikou KRPW-SS600W

Still havent decided on RAM or hard drive.  For RAM, I know that I need DDR3 DIMM, and I want either 2 or 4 GB to start, but what brand should I get?  I used RAM alright to buy?  

And the hard drive...I was originally going to go with Seagate, but Ive read some bad reviews.  What about Hitachi hard drives?  I need 500 GB...can anybody recommend one?

---

### Post by Jagoly on 2011-12-24
That Power supply seems good enough; 80+ bronze (according to google translate), and a 3 year warranty seems good enough.

My hard drives are all Western Digitals. Performance between drives of the same RPM from different brands is negligible. As for reliability, it's really luck of the draw. Some people will claim that every Seagate drive they've ever had has died, and that Hitachi is wonderful, others will have had the exact opposite experience. Just chose a new drive and avoid second hand drives. Most manufacturers provide a 3 year warranty (including Seagate and Hitachi), however WD's come with a 5 year warranty, hence why I choose them.

Ram is cheap now, so definitely go with 4gb as a minimum. You generally don't get "bad" ram, so just get what you can get get the best bargain for. High speed performance memory is only of interest to Overclockers (and less so on sandy bridge). The Kingston DDR3 Valueram I have in my server works well. If you can get second hand ram for free, than use that, but if not, buy some kingston. From my retailer, for example, a 2x2gb kit costs only $22.

---

### Post by kurt18947 on 2011-12-24
> **SnickerSnack said:**
> I have a GA-990FXA-UD3, and I think it is one of the newer models.  I'll try formatting in windows when I get access to a windows machine.  I usually make my flash drives fat, so I'll also try just formatting it NTFS (since I can do that now).

Edit: You must have not meant to format it as ntfs, but rather to use windows to format it to fat.  I'll do that when I can.  Thanks.

Correct, format to FAT(32).  NTFS won't work for a live USB, I don't believe.  I've tried formatting EXT2 and installing a 'regular'(non-live) Ubuntu install to a USB drive.  That didn't work either.

---

### Post by whatthefunk on 2011-12-25
Finished!  Typing this from my lightning fast new pc.  Running Kubuntu with no problems at all so far.  Heres the setup I went with:

Motherboard: ASRock Z68 Pro3
CPU: Core i5 2400 3.1 GHZ
Video card: Palit GeForce GTX 550 Ti Sonic
CPU Cooler: Scythe Mugen 3 SCMG-3000
CD/DVD: LG GH24NS7
PSU: Antec Earthwatts 650
HDD: WD 500 GB
4 GB RAM

Had a bit of a scare on first boot up....forgot to plug in the second motherboard power cable.  Other than that, it all went pretty smoothly.  And Kubuntu is beautiful!  Thanks for the help everyone!

---

### Post by Jagoly on 2011-12-25
YAY!!!

Hope this machine runs this great for years to come XD
May I ask what case you're using?

---

### Post by whatthefunk on 2011-12-25
Bought a Scythe Gekkou Silent Mid Tower Case.  It was on sale for $35.  Its good, but the front panel is put on with these weak plastic bits that Ive already managed to break two of.  It really is quiet...cant hear the fans running at all.

---

### Post by SnickerSnack on 2012-02-15
> **kurt18947 said:**
> Correct, format to FAT(32).  NTFS won't work for a live USB, I don't believe.  I've tried formatting EXT2 and installing a 'regular'(non-live) Ubuntu install to a USB drive.  That didn't work either.

I made a boot drive with a new usb drive (got a few SanDisk drives on the cheap) and it worked fine.  The filesystem was "W95 FAT32", or some rearrangement of those characters.  I'm writing this post from a crunchbang live session off that usb drive.

So, yes it would seem that some GA MBs only like to boot from usb drives formatted by/for windows.

---

### Post by kurt18947 on 2012-02-16
> **SnickerSnack said:**
> I made a boot drive with a new usb drive (got a few SanDisk drives on the cheap) and it worked fine.  The filesystem was "W95 FAT32", or some rearrangement of those characters.  I'm writing this post from a crunchbang live session off that usb drive.

So, yes it would seem that some GA MBs only like to boot from usb drives formatted by/for windows.

That is how it seems.  A liveUSB stick formatted with Ubuntu's disk utility and written with Unetbootin will boot perfectly on an older gigabyte MB or a Thinkpad notebook.  The same liveUSB stick will not boot on a rig with a newer gigabyte MB with an Award modular BIOS.  It will show a message like "boot error" or similar.  Reformat in windows 7, rewrite the live USB with Unetbootin and it boots fine.  I'd read someplace that the boot module of that BIOS was written by Microsoft.  I would not be surprised to learn that any "improvements" are undocumented.

---

