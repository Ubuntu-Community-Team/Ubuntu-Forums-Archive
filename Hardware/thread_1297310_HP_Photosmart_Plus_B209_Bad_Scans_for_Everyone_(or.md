---
title: "HP Photosmart Plus B209 Bad Scans for Everyone? (or just me?)"
date: 2009-10-21
forum: Hardware
---

### Post by jim_mule on 2009-10-21
hiya ubuntu peoples!
i just bought a brand new "HP Photosmart Plus All-in-One Printer series - B209", and its fantastic, at printing, and taking up space and making sound effects. but i cant seem to get good quality scans. poor definition and an almost semi thresholded like look to things. does anyone else have this model, and if so is it working ok for you? i dont have windows, so i cant even test this against windows. for the record im using jaunty and the latest hplip package from the hplip website. help please, i really dont wanna drag this beast back to the store and return on the hunt for a scanner which can work with linux. and i checked my sane settings quite well and all seems normal, no enhancements no gamma/contrast/etc. garbage.

---

### Post by Dark_Stang on 2009-10-21
Well, the scan quality on my girlfriend's desktop running Windows 7 is great with it. And the printing from my laptop running Ubuntu is great with it. I've never had a reason to scan with it though. Guess I'm gonna have to check that out today.

---

### Post by Giblet5 on 2009-10-21
Check your scan resolution.

Scanners have 'standard resolutions they really like' and you probably aren't scanning at that resolution.

Try 150, 300, 600, 1200, etc dpi...

HP's software for Windows *already knows* what resolutions that scanner likes. HP is cheap though and won't write the same software for Linux...

No matter. Use a standard resolution and you'll get the same results that you get under Windows.

A pic scanned at 300dpi under Windows will be as identical as it can possibly be with the same image scanned at 300dpi under Linux.

---

### Post by Dark_Stang on 2009-10-21
Well, I just tested out my B209a-m at 300 DPI on my girlfriend's avon catalog. Scanning across a wireless network it seems to work just fine and has very good quality. I just turned scanning up to 600 DPI and I can now see the individual dots made by the printer that made the catalog. Maybe your printer's scanner is defective.

---

### Post by jim_mule on 2009-10-21
thanks for the replies, ive tried 300 and 600 dpi. im scanning in drawings/paintings, and i notice a lack of tints/tones and subtle colors in general as well as an low line quality (details seem to get indistinct). will continue to look into it more. (im comparing scan quality to an old canoscan lide 40 that is 100% linux compatible, had one for years, then it busted while traveling, and if i look at an old drawing scanned with it compared to this, the quality is slack/rough. if your in berlin and wanna sell one of those old scanners, well i will pony up for one)

---

### Post by bob_apple on 2009-11-14
Oh defty defty!
We meet again!
I too just purchased one of these. And... yes it does appear to scan terribly. My Epson Perfection 1260 just broke and i picked one of these up. It a laughable comparison. Also, it does not seem to be able to pick up florescent at all. I just scanned a flor. pink and it looked pastel pink. ugh.

Looking up close(1:1) at the scans at 600 it looks compressed. I'm going to try scanning through hp-gui thing and see if there is a difference. All scans have been done with xsane inside of gimp.  I'm using debian not ubuntu but that prolly doesn't matter.

ps... padlaversusmoij.net(although i'm only on flickr these days)

I'll keep you posted.

---

### Post by bob_apple on 2009-11-14
Just tried hp-scan --compression=none --resolution=600

Still totally crap. It looks compressed when i zoom in. I don't have a windows system to test with either. Can someone out there who has one scan some written lines. With a pen or something and zoom in to 1 to 1. Cause right now is garbage.

---

### Post by jim_mule on 2009-11-14
hola bob apple, small internet round here isnt it. 
yeah i did a scan just using the hp itself, no software (lin or win) and had it put on a usb stick, when i looked at it, it was completely terrible, i do not know how they can make such terrible scanners. a friend of mine has a cannon which is similar, he says the printer would cost the same without it and they just slap the scanners on for office use, so documents and the ilk, but drawings or detail is lost. i hate to say it, but i am getting a new pc with windows on it for video editing and i am afraid i will also have to get a cheap decent scanner to go with it, i cant find any cheap current models of scanners that work 100% with sane.

---

### Post by bob_apple on 2009-11-14
ya... waste of money again. guess i'll just hop on ebay. but the thing is, my scans actually look like they are compressed with lossy compression. It's not just bad definition. It's actually compression. Almost like it only does an optical 75dpi scan and then digitally zooms it up to a higher dpi. Which kind of seems like they aren't really telling the truth(what a surprise) about the true resolution of it.

---

