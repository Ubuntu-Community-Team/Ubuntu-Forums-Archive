---
title: "8600m hardware issues fixed? THinking of buying a Vostro."
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by dogscoff on 2007-12-20
Hi,

I'm hoping to buy a new laptop in January. I intend to run Gutsy exclusively, so obviously Linux compatibility is a big factor in my choice of machine. I've tried manually installing drivers in linux before but it never seems to work for me so I'm hoping to find a machine that will run linux with minimal futzing about. 

The Dell Vostro 1500 series fits my specs and budget nicely, but they are only offered with NVIDIA GeForce Go 8600M graphics cards. Googling for this hardware + gutsy reveals a lot of driver issues, that apparently can't be fixed by manually installing/ tweaking drivers or using envy. Does anyone know if these issues have been resolved yet? If so, have the fixes made their way into the standard Gutsy installation? I would like to just run the latest Ubuntu install CD and have everything work out of the box. Is this likely to happen if I buy a Vostro 1500? Does anyone have experience to share with this hardware? 

On a related note, can anyone link to a list of *recent* laptops that "just work" from the gutsy install CD, or recommend a laptop? I find the process of picking a laptop with specs I like then checking each component for compatibility tedious, to say the least. Most "tested on linux" lists that I've found seem to focus on older hardware. Ideally I'd like to see a list of new laptops with either "works straight off the Gutsy CD" or "doesn't" next to them. 

I like the way you can customise the Dells prior to purchase, and I'm tempted by their pre-installed ubuntu machines, but I'd like a higher spec than the ones offered here in the UK. Lenovos are known for compatibility and durability (another bonus - I'm very clumsy!) and they do  look nice but they are very pricey.  I'm hoping to find a laptop with either a fast processor or dual-core processor (of course both together would be nice=-), at least 2 gig of ram and a graphics card that uses its own dedicated ram, rather than poaching from system memory. I don't care what the brand is, as long as it works.  Budget is about £600-£700. Screen size 14 or preferably 15 inch. Won't be travelling with it too much so a 17" would be OK. 

Thanks for reading.

---

### Post by jespdj on 2007-12-20
I have a desktop PC with a 8600 GTS and a laptop with a 8400M GS. Both work without any problems - after installing Ubuntu 7.10, activating the nVidia restricted driver was no more effort than clicking a button and everything works without any problem.

Gutsy works great on the Dell XPS M1330. Everything on my M1330 works out-of-the-box, except for one thing: the internal microphone. But there's a fix for that, which was easy to install. For the specs, see my signature below.

Note: You can find Dell-specific Ubuntu bugs here: [https://bugs.launchpad.net/dell/](https://bugs.launchpad.net/dell/)

---

### Post by dogscoff on 2007-12-21
> **jespdj said:**
> I have a desktop PC with a 8600 GTS and a laptop with a 8400M GS. Both work without any problems - after installing Ubuntu 7.10, activating the nVidia restricted driver was no more effort than clicking a button and everything works without any problem.

Gutsy works great on the Dell XPS M1330. Everything on my M1330 works out-of-the-box, except for one thing: the internal microphone. But there's a fix for that, which was easy to install. For the specs, see my signature below.

Note: You can find Dell-specific Ubuntu bugs here: [https://bugs.launchpad.net/dell/](https://bugs.launchpad.net/dell/)

Thanks very much, that's great news. The XPS 1330's screen is a little small for my taste, but the 1530 would be great.

Thanks again.

---

### Post by Vadi on 2007-12-22
For completely tux-friendliness, check out system76.com and zareason.com.

I'm eyeing that laptop myself right now (the vostro), hm..

---

### Post by dogscoff on 2008-01-03
Thanks for the URLs, Vadi. Machines look nice, but neither of them ship to the UK.

I'm now tempted to wait until this news: [http://hardware.slashdot.org/article.pl?sid=07/12/22/076211](http://hardware.slashdot.org/article.pl?sid=07/12/22/076211) starts either making 4gig laptops more affordable, or causes manufacturers to dump the price on their 2 gig machines in order to clear stock. 

I don't suppose anyone has any informed opinions as to when that might happen?

---

### Post by Vadi on 2008-01-03
I think these guys ship in UK: [http://efficientpc.co.uk/](http://efficientpc.co.uk/)

---

### Post by henriquemaia on 2008-01-03
I have a laptop (compal IFL90) with Nvidia's 8600m card and I had some freezing issues using the Ubuntu installed driver. After several attempts to solve these annoying crashes that occurred a lot while playing games, I installed the latest Nvidia drivers through [Envy]("http://albertomilone.com/nvidia_scripts1.html") and now everything is working like a charm.

---

### Post by dmgthe2nd on 2008-01-03
I own a vostro 1500 with Gutsy installed on it.  I installed Feisty to begin with and just updated through ubuntu to 7.10.

Here are my unresolved issues:
The sound:  When you boot with no headphones plugged in, the speakers will work all the time (even with a pair of headphones plugged in).  But when you boot with headphones plugged in, the speakers won't work at all until the next boot.

Minor glitch:  Sometimes my computer freezes when the desktop (gnome) is loading.  There are missing app. buttons or just no background.  Time does not resolve that issue.

Getting the wireless and sound to work is not that hard, there are a few very useful threads on this forums regarding the Vostro 1500 specifically.  Also, I have the nVidia 8600 video card and I have had no problems with it on Gutsy and Feisty.  You get consistent 1440x900 resolution :)

You can probably find a better machine for Ubuntu but IMO the vostro 1500 is a solid machine with good specs at a decent price.

---

### Post by dogscoff on 2008-01-04
> **Vadi said:**
> I think these guys ship in UK: [http://efficientpc.co.uk/](http://efficientpc.co.uk/)

They do, and I'm very tempted by their machines, the price and spec is very nice indeed for me. The only thing that worries me is this, from their laptop spec page:

"Graphics: Nvidia 8600M GS 256MB memory (Supported by lastest nvidia driver, **manual install**)" (My emphasis)

Which brings me back to the top of this thread. How much trouble is it to install the driver for this graphics card? Why does the manufacturer of the Anubis (which comes pre-loaded with Ubuntu) wants me to install it for myself? If it's too difficult for them, there's no way I can do it.

---

### Post by Vadi on 2008-01-04
I see.

Email and ask them why?

Though I recommend Envy to anyone with driver problems, and it solves those real well.

---

### Post by dogscoff on 2008-01-04
> **Vadi said:**
> I see.

Email and ask them why?

Though I recommend Envy to anyone with driver problems, and it solves those real well.

I've emailed them, I'll report back here when I get news. I also looked up the driver installation advice on nvidia's site and it *looks* simple enough: 
[http://www.nvidia.co.uk/object/linux_display_ia32_100.14.09_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_100.14.09_uk.html) one line in the console and then mucking around with some kind of X config GUI. Whether it actually works as advertised or not (probably does for everyone but me=-) remains to be seen...

---

### Post by henriquemaia on 2008-01-07
> **Vadi said:**
> 

Though I recommend Envy to anyone with driver problems, and it solves those real well.

I second that.

---

### Post by dogscoff on 2008-01-09
> **dogscoff said:**
> I've emailed them, I'll report back here when I get news. I also looked up the driver installation advice on nvidia's site and it *looks* simple enough: 
[http://www.nvidia.co.uk/object/linux_display_ia32_100.14.09_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_100.14.09_uk.html) one line in the console and then mucking around with some kind of X config GUI. Whether it actually works as advertised or not (probably does for everyone but me=-) remains to be seen...


Efficientpc responded, apparently the driver information on their site is out of date. No manual installation required!!! Looks like they've updated their website, too. 

I think I will definitely be buying an Anubis with Gutsy pre-installed: [http://efficientpc.co.uk/laptops/anubis/](http://efficientpc.co.uk/laptops/anubis/)
Can't wait!

Thanks for the help everyone, I have another question now but I'll start a new thread for it.

---

