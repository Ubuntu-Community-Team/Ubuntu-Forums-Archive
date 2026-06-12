---
title: "Installing Ubuntu to ThinkPad Chromebook"
date: 2018-08-14
forum: Hardware
---

### Post by mvblair on 2018-08-14
Hi There,

Before I jump into the water, I wanted to seek some advice. 

I would like to get a laptop for word processing that starts up and allows me to get typing quickly. I am interested in getting a refurbished or used ThinkPad Chromebook, possibly from Lenovo's website or eBay. Something under $200. 

I am worried about the install process. Maybe eight years ago I installed Ubuntu on a Sony Vaio that was running Windows. I'm not very good with computers and I've probably gotten worse since then, but I really liked Ubuntu. I have been looking at the instructions on [the Ubuntu tutorials website here]("https://tutorials.ubuntu.com/tutorial/install-ubuntu-on-chromebook#0"). 

It looks like the process of installing Ubuntu has gotten easier, but what are the chances of having hang-ups, especially from a Chromebook? Are the ThinkPad Chromebooks pretty reliable for installing Ubuntu? Are there models I should watch out for (besides the usual caveats that go with getting something refurbished)? 

Lastly, I am not very interested in having a dual-boot system. I think I would like to forget about Chrome. After Ubuntu is installed, is it hard to set it up so that Ubuntu runs automatically when I turn it on? 

Any advice would be appreciated. Thank you! 

Matt

---

### Post by TheFu on 2018-08-14
The link for instructions you have provided will still be running ChromeOS. Every few weeks it will break when Google forces an update.  You'll need to update the crouton install before it works again and sometimes the crouton update isn't ready for a few days.
You'll boot into chromeOS, open a terminal and type a few commands to get any Linux version running inside a chroot.  You will see Chrome every time.

If you want to wipe chromeOS and boot directly into a Linux, then ... keep reading.

Making a chromebook be installable for any Linux is a non-trivial exercise.  Different models have different issues, so saying "Lenovo" isn't enough.  Some are easier than others.  Some are impossible.  $200 for a used chromebook is way too high, IMHO, especially if you just want word processing.

I'm on my 3 chromebooks.  The keyboards keep wearing out, usually before 2 yrs.  On most laptops, changing the keyboard is $20 and 10 minutes of effort.  Not so for chromebooks where it is more like $100+ and half a day. Pulling the entire machine apart, including the motherboard, is required.

The easiest chromebooks to get working with Linux are listed at mr. chromebox's website [https://mrchromebox.tech/#devices](https://mrchromebox.tech/#devices) .  I have personal experience with a Acer C720 and Toshiba CB2.  The Acer was really easy.  The Toshiba took much more effort and still  requires effort to maintain it due to BIOS differences.
 After breaking the warranty (you'll have to do that on every chromebook), then you flash a replacement BIOS, and can load almost any OS, if the chromebook is intel-based.  The chromebook will never boot chromeOS again, ever.

A friend had a Lenovo chromebook that took over a year to get Linux onto. It was cheap when he bought it ($99 new) and he got paid $50 for a battery class action lawsuit, so the price was $49 total.  It is a dog with a very slow CPU.

Oh and any CPU you get should have a passmark rating of about 1500 or more. A Celeron 2950U is fairly old now, but a fast CPU in a chromebook.  Many of the newer models have CPUs that are over 50% slower than that. Be careful.  ALWAYS check the exact CPU so you aren't sorry.

There are low-end laptops available these days which will run Linux without all the same hassles.  They won't be missing certain keys that all chromebooks lack - DELETE, F11, F12, PgUp/Dn/Home/End ... you get the idea. I don't plan to ever buy a chromebook to run Linux again now that cheap laptops exist.  There are some great, fast, used Lenovo laptops on ebay.  I'm  partial to Dell myself - prefer the Dell keyboards.

Those are my experiences.  Hopefully, others will chime in with their experiences. I'm only 1 data point.

---

### Post by mvblair on 2018-08-15
Fu, I really appreciate your reply. You're helping me figure out what I really want. I am disappointed to hear that you've not had a good experience with the Chromebooks. I imagine that it would be worse for me. What you're saying is that besides the fact that the keyboards wear down, there are multiple issues with getting Linux on them. I don't think I can do much more than do a few copy-and-pastes in order to get Ubuntu installed, so it sounds like a Chromebook probably isn't the way to go. Not as easy as clicking the link I posted. 

Reading between the lines, I think your opinion is that getting a regular Windows laptop would be better for my purposes. You're saying it's just less of a hassle and less of a risk to get Ubuntu on them. 

I have my heart set on the ThinkPad brand because I like the keyboards. I was thinking about Chromebooks because their battery charge versus cost seems to be fantastic. Based on your comment about the keyboard though, I might check out a Dell brand as well. And just thinking this through as I write, you've convinced me that a Chromebook is not the way to go though. 

Hey, I really appreciate your thoughts and you taking the time to reply. It really does help me be a better consumer and figure out what is best for me. 
> **TheFu said:**
> The link for instructions you have provided will still be running ChromeOS. Every few weeks it will break when Google forces an update. You'll need to update the crouton install before it works again and sometimes the crouton update isn't ready for a few days.
You'll boot into chromeOS, open a terminal and type a few commands to get any Linux version running inside a chroot. You will see Chrome every time.

If you want to wipe chromeOS and boot directly into a Linux, then ... keep reading.

Making a chromebook be installable for any Linux is a non-trivial exercise. Different models have different issues, so saying "Lenovo" isn't enough. Some are easier than others. Some are impossible. $200 for a used chromebook is way too high, IMHO, especially if you just want word processing.

I'm on my 3 chromebooks. The keyboards keep wearing out, usually before 2 yrs. On most laptops, changing the keyboard is $20 and 10 minutes of effort. Not so for chromebooks where it is more like $100+ and half a day. Pulling the entire machine apart, including the motherboard, is required.

The easiest chromebooks to get working with Linux are listed at mr. chromebox's website [https://mrchromebox.tech/#devices](https://mrchromebox.tech/#devices) . I have personal experience with a Acer C720 and Toshiba CB2. The Acer was really easy. The Toshiba took much more effort and still requires effort to maintain it due to BIOS differences.
After breaking the warranty (you'll have to do that on every chromebook), then you flash a replacement BIOS, and can load almost any OS, if the chromebook is intel-based. The chromebook will never boot chromeOS again, ever.

A friend had a Lenovo chromebook that took over a year to get Linux onto. It was cheap when he bought it ($99 new) and he got paid $50 for a battery class action lawsuit, so the price was $49 total. It is a dog with a very slow CPU.

Oh and any CPU you get should have a passmark rating of about 1500 or more. A Celeron 2950U is fairly old now, but a fast CPU in a chromebook. Many of the newer models have CPUs that are over 50% slower than that. Be careful. ALWAYS check the exact CPU so you aren't sorry.

There are low-end laptops available these days which will run Linux without all the same hassles. They won't be missing certain keys that all chromebooks lack - DELETE, F11, F12, PgUp/Dn/Home/End ... you get the idea. I don't plan to ever buy a chromebook to run Linux again now that cheap laptops exist. There are some great, fast, used Lenovo laptops on ebay. I'm partial to Dell myself - prefer the Dell keyboards.

Those are my experiences. Hopefully, others will chime in with their experiences. I'm only 1 data point.

---

### Post by TheFu on 2018-08-15
I have had good experiences with chromebooks, for the price and the time (date). 2013 was a different time.  I've gone from a $0 netbook (gift from a relative) to a chromebook that easily ran Ubuntu-Openbox.  I was personally frustrated by the low resolution, 768p, 11inch, and that my typing wore out the keyboard.  Many people are fine with that resolution and do not wear out keyboards.

All chromebook keyboard layouts are the same. Missing DELETE, F11, F12, Home/End/PgUp/PgDn keys.

I moved to a 2x faster CPU, 2x more RAM, 14inch, and 1080p chromebook. Again, the keyboard wore out much earlier than I like. I'm using it now with 4 nonworking keys, which makes it difficult, sometimes. It also requires a completely new BIOS to run Linux and that BIOS doesn't follow the UEFI standards for booting.  Besides those things, I love this machine.  Both left & right arrow keys require lots of attempts to work at all and the left CNTL and left ALT keys haven't worked in months.  With 1 virtual manage management took, left-CTL+left-ALT are used to break out of a VM.  Very frustrating.  Remapping the hot-key to something else has failed.

But this is 2018 and there are cheapish laptop options today.  For long battery life, perhaps a cheap android tablet and keyboard would be a better option for your wordprocessing requirement.  $50 for an Amazon 8in tablet isn't bad.  You can remove many of the nags and disable the privacy sucking aspects.   It can't be root'd, so we are stuck with whatever OS Amazon wants to push with that model.  I have one, but have blocked amazon stuff at the network firewall, never enabled the google store, I prefer the F-Droid store with mainly GPL programs. 

Just a thought.

I mainly use my chromebook running Ubuntu+openbox for remote access back to real computers which are much more capable.  From almost anywhere in the world, I can access my desktop running on Core i7 desktop hardware for doing "office" things.  No video and no audio,but there are other solutions for that (web browser interface into Plex media server).  I've done this from 5 continents.  For my needs, Android just wasn't enough OS.  I tried on a European trip for 3 weeks, back in 2012-ish, and it failed to meet my needs. Since then, I've carried a linux laptop.  Oddly, in 2008, I had a tiny Linux tablet that worked fantastic for a 2 month trips in Asia and another in Central & South America, but rumors that Microsoft killed that company (nokia) and the linux-based line of products on purpose have never been proven.  [https://www.theguardian.com/technology/2014/apr/29/stephen-elop-microsoft-nokia](https://www.theguardian.com/technology/2014/apr/29/stephen-elop-microsoft-nokia) regardless of my personal opinion.

Lots of options these days.  If you have $200, get a used Lenovo/Dell laptop and load Ubuntu. Both of those vendors have a history of good compatibility with Linux distros.  If you have $100, get a used Acer Chromebook,check the CPU exactly for performance, but be prepared for some effort to make it work.  Of course, prices will be different depending on where in the world you happen to be located.   I found a Dell laptop for $160 just now with a Core i3 CPU. [http://www.microcenter.com/product/510533/latitude-e5430-14-laptop-computer-refurbished---black](http://www.microcenter.com/product/510533/latitude-e5430-14-laptop-computer-refurbished---black) That's just 1 example.  Watch out for HP & Acer laptops. Manual UEFI stuff has been necessary for installation.  There was a Lenovo, but it had a terrible AMD E450 APU.  Gotta check the specs, always.

---

### Post by kc1di on 2018-08-15
If it were me I would go for a rebuilt Lenovo T430 for about the same money. [Here]("https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&Description=t430&N=-1&isNodeId=1") is one possibility.

---

### Post by mvblair on 2018-08-15
> **TheFu said:**
> All chromebook keyboard layouts are the same. Missing DELETE, F11, F12, Home/End/PgUp/PgDn keys. This fact totally escaped me when I used Chromebooks. Because I just want to do word processing, I can't imagine not have page up, page down or the delete key. Even if the prices are good, that kind of rules out Chromebooks for me (besides the matter of installing Ubuntu). 

> I moved to a 2x faster CPU, 2x more RAM, 14inch, and 1080p chromebook. Again, the keyboard wore out much earlier than I like. I'm using it now with 4 nonworking keys, which makes it difficult, sometimes. It also requires a completely new BIOS to run Linux and that BIOS doesn't follow the UEFI standards for booting.  Besides those things, I love this machine.  Both left & right arrow keys require lots of attempts to work at all and the left CNTL and left ALT keys haven't worked in months.  With 1 virtual manage management took, left-CTL+left-ALT are used to break out of a VM.  Very frustrating.  Remapping the hot-key to something else has failed. For me, this is like saying, "besides that, how was the play, Mrs. Lincoln?" I just don't have the ability to put in a new BIOS or whatnot. 

> But this is 2018 and there are cheapish laptop options today.  For long battery life, perhaps a cheap android tablet and keyboard would be a better option for your wordprocessing requirement.  $50 for an Amazon 8in tablet isn't bad.  You can remove many of the nags and disable the privacy sucking aspects.   It can't be root'd, so we are stuck with whatever OS Amazon wants to push with that model.  I have one, but have blocked amazon stuff at the network firewall, never enabled the google store, I prefer the F-Droid store with mainly GPL programs.  I'm getting off topic, but I had one of these Amazon tablets, an older version. Supposedly there was a work around to put a stock version of android on it, but I couldn't get it to work. Even after turning off all these awful ads and nags, I just didn't enjoy using it. 

> Lots of options these days.  If you have $200, get a used Lenovo/Dell laptop and load Ubuntu. Both of those vendors have a history of good compatibility with Linux distros.  If you have $100, get a used Acer Chromebook,check the CPU exactly for performance, but be prepared for some effort to make it work.  Of course, prices will be different depending on where in the world you happen to be located.   I found a Dell laptop for $160 just now with a Core i3 CPU. [http://www.microcenter.com/product/510533/latitude-e5430-14-laptop-computer-refurbished---black](http://www.microcenter.com/product/510533/latitude-e5430-14-laptop-computer-refurbished---black) That's just 1 example.  Watch out for HP & Acer laptops. Manual UEFI stuff has been necessary for installation.  There was a Lenovo, but it had a terrible AMD E450 APU.  Gotta check the specs, always.This laptop looks very attractive. I think it can more than handle LibreOffice. I didn't realize there were relatively new, albeit refurbished, standard laptops under $200. I guess the Chromebooks must have pushed the prices and the specs down for this market? The battery for that Dell has gotten good reviews. Thank you for the tip! 

Matt

---

### Post by mvblair on 2018-08-15
> **kc1di said:**
> If it were me I would go for a rebuilt Lenovo T430 for about the same money. [Here]("https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&Description=t430&N=-1&isNodeId=1") is one possibility. That's also a good tip. Thank you. I do like the look of that keyboard!

---

