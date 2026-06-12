---
title: "Component Compatibility with Ubuntu Server"
date: 2017-08-07
forum: Hardware
---

### Post by csaltrev on 2017-08-07
I'm planning on building a small business server that'll host a  lightweight database (H2 Java database), and will be concurrently accessed by about 5  people. It will possibly be utilized as a file server as well.

Ubuntu Server is my operating system of choice for this server build.  However, I'm quite skeptical on the compatibility of the parts of choice  with the operating system, particularly on the motherboard (Gigabyte  GA-B250M-DS3H).

The Ubuntu Server version I intend to install is 16.04.3.

The following parts list was elaborated with future upgrades in mind. If  there exist issues with the motherboard or any other component, please  let me know. Further suggestions and/or modifications to the component  list are appreciated as well.

List: [Server]("https://pcpartpicker.com/list/wLJ2sJ")

Thanks in advance,
Carlos

---

### Post by vocx on 2017-08-09
> **csaltrev said:**
> I'm planning on building a small business server that'll host a  lightweight database (H2 Java database), and will be concurrently accessed by about 5  people. It will possibly be utilized as a file server as well.

Ubuntu Server is my operating system of choice for this server build.**  However, I'm quite skeptical on the compatibility of the parts of choice  with the operating system, particularly on the motherboard (Gigabyte  GA-B250M-DS3H).**

Why are you skeptical? What would cause problems? Essentially in a modern Linux system the only problem you may experience is due to the graphics drivers, if you are planning on using a dedicated Nvidia or AMD/ATI graphics card. Everything else should work. A CPU always works; RAM, and hard disk should work. Power supply, case? These don't even interact with the operating system, they just work.

If your motherboard includes a normal integrated Intel graphics card I don't think you will experience any problems. It normally uses a pretty standard driver "i915", which is already included in Linux, so you shouldn't have a problem. Also, I guess, you won't try running games in that machine, so you don't need to bother with a dedicated video card.

---

### Post by oldfred on 2017-08-09
I installed desktop to Gigabyte Z170 which really is very similar to Z270.

Discussion is more about a server install in UEFI mode:
[https://ubuntuforums.org/showthread.php?t=2315007&page=2&p=13449024#post13449024](https://ubuntuforums.org/showthread.php?t=2315007&page=2&p=13449024#post13449024)

---

### Post by csaltrev on 2017-08-09
> **vocx said:**
> Why are you skeptical? What would cause problems? Essentially in a modern Linux system the only problem you may experience is due to the graphics drivers, if you are planning on using a dedicated Nvidia or AMD/ATI graphics card. Everything else should work. A CPU always works; RAM, and hard disk should work. Power supply, case? These don't even interact with the operating system, they just work.

It's my first time installing Linux OS on a clean build, hence the skepticism. I was inaccurate in my question since I did not specify the components which I doubted of their compatibility, and simply added a link to the full list of components. Either way, thanks for the remarks.

> **vocx said:**
> If your motherboard includes a normal integrated Intel graphics card I don't think you will experience any problems. It normally uses a pretty standard driver "i915", which is already included in Linux, so you shouldn't have a problem. Also, I guess, you won't try running games in that machine, so you don't need to bother with a dedicated video card.

I emphasized the motherboard since--on its manufacturer webpage and on retail websites--the specified compatible operating systems are only Windows. Then again, since you think a motherboard with an Intel CPU/integrated GPU won't cause trouble, I'll go forward.

Thanks for your response.

---

### Post by vocx on 2017-08-09
> **csaltrev said:**
> 
I emphasized the motherboard since--**on its manufacturer webpage and on retail websites--the specified compatible operating systems are only Windows**. Then again, since you think a motherboard with an Intel CPU/integrated GPU won't cause trouble, I'll go forward.

Thanks for your response.
Manufacturer webpages and retail webpages typically ignore Linux in every way. Their systems may run Linux without problems, however they don't mention this. It's their marketing strategy; they focus on the big market that Windows users represent. I don't understand it. I'd think saying "Linux compatible" would appeal to a bigger market, that is, both Windows and Linux users.

However, the fact that Linux is open source, and not centralized, that is, developed by multiple parties, brings into question who provides support. If the system does not work, whom should I blame? So, that's why they don't advertise Linux compatibility, they don't want to take responsibility if their system doesn't actually work with Linux.

But yeah, generally speaking, Intel hardware is very friendly with Linux, it just works.

The problems are mostly caused by
[LIST=1]
[*]new Nvidia or AMD/ATI video cards which are intended for playing games in Windows, and thus may not have good drivers in Linux; and
[*]the multitude of different WiFi cards available in the market. There are many, many different cards, USB dongles, and adapters out there. If you are buying an additional Wifi card, browse the web for success stories on Linux, before you buy.
[/LIST]

---

