---
title: "cant instal from usb boot with new emmc  netbook - asus vivobook e203m"
date: 2019-02-21
forum: Hardware
---

### Post by mtlinix on 2019-02-21
ive been using lubuntu and tinycore on an old acer aspire one for  a few years, and decided to get a newer netbook.
i bought an asus vivobook e203m on amazon a few days ago, was 150 pounds new on sale, with an n4000 cpu and 4gb ram and emmc drive.

went to instal lubuntu yesterday from a usb boot, as i had done many times with my old acer, and i couldnt instal it.

i would go to boot menu after a restart and see the choices for emmc, usb or enter bios/uefi settings i would select the usb, and it just would either load windows from the emmc drive anyway, or if i tried restarting and going to boot menu after disabling the emmc drive in uefi so that only the usb option was available in the boot menu, the netbook would just stay black screen until i switched it off. choosing usb as primary boot in bios and letting pc restart also does nothing, just loads emmc with windows.

i had already read on forums that i had to change a few settings in uefi such as disable fast boot and secure boot, any version of these settings didnt help. i did a lot of googling - mostly found info and posts about slightly different models, nothing on this exact model i could find really.


i contacted asus tech support earlier, and was told that all emmc laptops cant boot from usb.
i explained that im sure some can and do, and was then told that this model definitely cant boot from usb.
i asked if there was a link to any info on this, just so i could be sure there wasnt some confusion and i was told "no, it was internal asus info not availabe to public"?? they did say someoen would get back to me, but noone has yet.

anyway i am returning this laptop because it actually does have a very loose and annoying trackpad, although i still want to know if its possible to install linux on that model - vivobook e203m
i want to buy another netbook possibly same model, or similar spec.
 of course i i dont want to buy a netbook that i cant instal linux on, but i did want to buy a recent netbook model, new. this e203m model one would be perfect with linux for my use.
 
does anyone have any answers about this , or even suggestions for an alternative similar netbook? im happy with small screen, 8.9 or 11.6 etc, no bigger really and i wanted 4gb ram and n4000 cpu and ssd at around 200 pounds(or less).
that asus actually has a nice screen, non reflective. i see chrome bosk are cheap but it seem sdifficult to get linux on those too from what ive read.

im a very basic user, while i did work out how to intsall and use tinycore, which was at first very confusing to me, i havent gone beyond that really. 
i just use netbook as media centre, web, vlc, gimp, libre etc.  i get a bit confused by forum posts sometimes -  im hoping any possible replies wont be too complicated or assume i know more than i do about computers.
i like using netbooks and running tinycore or lubuntu and its always been easy enough to get them installeds previously with my acer aspire zg5 and other more recent acer aspire i5 laptops, 
 i was really dispointed with myself for not being able to work it out, but now im realising it may not be my fault.

also - is this something that computer makers are intentionally doing to stop people getting the best value from low spec pcs? making it difficult boot a new os from external usb drive? 
is there another way to get linux on a netbook like mine, thats seems to have an emmc that at least offically "doesnt boot from usb" ?

---

### Post by oldfred on 2019-02-21
Review that shows comparisons to similar systems.
[https://www.laptopmag.com/reviews/laptops/asus-vivobook-e203na](https://www.laptopmag.com/reviews/laptops/asus-vivobook-e203na)

Some other Asus models, seem to be higher end.
       Asus Vivobook S15
[https://ubuntuforums.org/showthread.php?t=2375408](https://ubuntuforums.org/showthread.php?t=2375408)
ASUS VivoMini UN45 UEFI update required to see NVMe drive
[https://ubuntuforums.org/showthread.php?t=2355295](https://ubuntuforums.org/showthread.php?t=2355295)
[https://ubuntuforums.org/showthread.php?t=2402972](https://ubuntuforums.org/showthread.php?t=2402972)

---

### Post by tea for one on 2019-02-22
I'm a bit surprised that your Asus netbook prevents you from installing Ubuntu or similar so I had a quick look around to see what I could find.

I was particularly interested because I had also contemplated the purchase of the same device.

I notice that you purchased from Amazon UK but I found some reviews on Amazon USA which indicated that you could boot from a usb device.

There is a possibility that the specification is different between USA and UK but nevertheless, here is the link:-

[https://www.amazon.com/VivoBook-Celeron-Processor-Storage-E203MA-YS03/dp/B07CTKRPGK](https://www.amazon.com/VivoBook-Celeron-Processor-Storage-E203MA-YS03/dp/B07CTKRPGK)

Pop the word **linux** in the Amazon "Have a question" search box for the Asus netbook on the above link.

[https://errorcodespro.com/asus-boot-from-usb/](https://errorcodespro.com/asus-boot-from-usb/)

Hopefully, it may help.

---

### Post by mtlinix on 2019-02-23
thanks for both responses, i checked the info you linked.
@tea  i hadnt seen that amazon question but i had seen the link that was shown by 1 user there. i do see the asus support replying on amazon stating that linux "not recommened" theyre calling it e203ma, it did say e203ma on the box i got.

im able to see the usb, and "select" it, it just doesnt load from it just loads the windows up or nothing.
in this netboosk uefi, it doesnt have a legacy boot mode, option or option to enable csm thats shown as the solution in some posts on the general topic. 
i guess what i didnt try was update the uefi and test it then, since that seems to be something mentioned reading it back.

ive actually sent the product back to amazon for the loose mousepad issue but i would consider it again, if i knew i could acces legacy boot + csm from an update, or whichever method is needed to get  usb boot to work 
there is a lenovo s130 with similar spec and cost im looking at now too, following on from a link fred posted. lenovo s130, 11.6, 4gb, emmc, n4000, that happens to be 170 pounds on sale . i think that is ok for linux usb boot, but still not 100% sure.

the tech support staff i spoke to previously assigned someone to  get back to me and this is the relevant paragraph of an email i  received this morning:
"We do apologize for the inability to boot from USB but can confirm  that this is not possible base on design. Please be advise that your  model supports only Windows 10 and no other OS. Therefore your only  resolve would be to perform Recovery using Windows Runtime  Environment to execute Factory Reset. You may also contact your region  of support to make further enquiries as to why this is the case." 

i havent made further enquiry anyway, if i decide i want this e203m netbook again i will enquire. 
if theres anyone else with an asus e203m uk model whos had a similar issue and worked it out (or didnt) by flashing the ufei bios let us know.

---

### Post by oldfred on 2019-02-23
Some of these very lightweight systems were 64 bit but used a 32 bit UEFI. They were designed when Linux did not have a 32 bit UEFI, so they planned to have a proprietary system with Windows only.
For those systems you have to add a 32 bit UEFI to boot installer and then the install.

       32 bit UEFI
[https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc](https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc)
[https://askubuntu.com/questions/392719/32-bit-uefi-boot-support](https://askubuntu.com/questions/392719/32-bit-uefi-boot-support)

---

### Post by AnotherBrian on 2019-02-24
maybe butting in here on something i don't know about.&nbsp; i believe uefi assures that the hardware is locked to an instance of the os.&nbsp; so if someone swaps the drive, the bios will block the boot.&nbsp; (Im guessing your drive is soldered to the motherboard.).&nbsp; If that is so, then you have to use bios to get into legacy mode. &nbsp;&nbsp; maybe this is under advanced settings but I saw some versions of bios do this on boot options.&nbsp; it might show "boot mode [uefi]".&nbsp; That is where you need to edit it to legacy. &nbsp; with this understanding if you can't get to legacy mode then no way to update.&nbsp; (BTW - I looked at a teardown video of your system and it looks like there is no removable hd / ssd.&nbsp; so I would assume those chips are soldered on.)<br>

---

### Post by CarlGWatts on 2019-04-25
I bought an ASUS Vivobook E203M (Celeron N4000, 4GB, 32GB eMMC) and installed XUbuntu 18.10 on it the normal way and it works just fine.  I updated to XUbuntu 19.04 this morning and that seems to work just fine as well.  XUbuntu is very snappy on it, I'm quite pleased.  Even Suspend works correctly.  I noticed there seems to be some problem getting the screen to wakeup after the screen goes to sleep but that is the only problem I've seen so far.  I'm looking for the solution to that problem now.
I didn't need to change any setting with UEFI boot ROM, XUbuntu just boot from my USB stick and worked correctly.

---

### Post by him610 on 2019-04-26
Amazon says it has a newer model, [https://www.amazon.com/ASUS-Ultra-Thin-Processor-Microsoft-L203MA-DS04/dp/B07N6S4SY1/ref=dp_ob_title_ce]("https://www.amazon.com/ASUS-Ultra-Thin-Processor-Microsoft-L203MA-DS04/dp/B07N6S4SY1/ref=dp_ob_title_ce")

---

