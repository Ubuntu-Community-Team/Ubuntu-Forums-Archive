---
title: "NVIDIA vs Intel graphics on Lenovo T410/T510"
date: 2010-10-16
forum: Hardware
---

### Post by sevenflo on 2010-10-16
I'm looking into buying a customized to order Lenovo Thinkpad (either the T410, T410s, or maybe T510).

Here's my issue: my last two laptops have died because of the NVIDIA card (probably heat damage). I don't game at all, and my main uses are web design, GIMP, photos, school/notes, server management etc. 

Am I better off with an NVIDIA graphics card or "Intel HD" integrated graphics chip?

I like to use Compiz. Will I have issues if I use compiz with integrated intel graphics?

Personally, I'd like to avoid any discrete graphics chip at the moment, unless there are proper NVIDIA drivers which allow me to manipulate my brightness keys without weird quirks (cough, Sony Vaio FZ).

Any other input on the above models?

---

### Post by P4man on 2010-10-16
I have both ( i mean intel IGP and nvida IGP, not those specific models). 

First, let me say the intel machine I have (X3100) works just fine. Its the first intel IGP I ever had and, and its okay at compiz, its surprisingly good at videoplayback (xbmc, flash, ..), no issues, great battery life. Its horrible at anything 3D. Performance is even worse than I feared, and I wasnt expecting much. If you are REALLY sure you wont ever need fast 3D, go for it. But buyer beware. 

As for nVidia; the bumpgate fiasco that probably bit you has been solved for some time now. Any recent nVidia chip should last as long as any other chip. Driver support is excellent as you know, VDPAU, good 3D, etc. You do pay for that in battery life.  

Lastely, brightness control isnt a driver issue, its a bios/acpi issue. Blame sony, not nvidia for that.

---

### Post by cbemerine on 2010-10-16
Its frustrating to have hardware problems and there have been many gotchas with various proprietary vendors over the years.  Even though there are more device drivers for Linux than any other operating system in the history of PCs (and I have used most of them) occasionally one proprietary vendor or another gets stupid and artificially limits their hardware's ability to work with Linux.  We all know ($$$) their reasons.  You can search online for those that have been caught over the years. 

The point is this, hardware problems can be avoided today with 99% certainty.

I have not had problems with WiFi, GPUs (Nvidia), Video (codecs), Audio (Pusle Audio vs anything) in years for one simple reason.  I only purchase hardware from Linux vendors, no more big box stores.  With a Linux vendor you KNOW the hardware will work with any distro of Linux you want to run. 

My favorite two are ZaReason and System76.  I have met the owners of ZaReason as they attend ScALE in Los Angeles each year.  

Note: ScALE is a great and inexpensive Linux conference.  Not many conferences that you can go to with so much information where attendance is under $100.

I do not work for any Linux vendors currently.  And while I currently have no interest in running other operating systems, I know I can run them on the hardware I purchase from these vendors.  (*I wish it were always true the other way around, that if you purchased proprietary hardware it would always work with Linux, sadly that has proven not to be the case over the last decade plus some more years.*) Often the prices are cheaper, even after shipping, as they know that they have to be competitive to get and earn your business.  However even if it cost a little more, it would be worth it to sleep well at night.  

Once you have hardware that you KNOW will work with Linux, the only thing that can happen would be for you to install an unstable release of software over top of one that is working.  Thankfully this can be undone and fixed a heck of allot easier then hardware problems.

I can highly recommend ZaReason to anyone and everyone and they stand behind their warranties.  Linux vendors know which of Nvidia's and Intel's products work best with Linux and avoid their problem child product offerings.

---

### Post by sevenflo on 2010-10-16
Thanks for both of the replies.  I hadn't heard of bumpgate, perhaps that was the cause of the heat.

Anyhow, it's good to hear that if I choose NVIDIA for my lenovo, it shouldn't cause a problem (hopefully) as my main issue was a BIOS one. 

Thanks for the help!

---

### Post by sevenflo on 2010-10-19
@P4man
Am I likely to experience any issues with "automatic switchable graphics" ?

A friend of mine had experienced issues (granted, with an earlier version of Ubuntu) and I'm not sure how this is handled in 10.04.

Thanks.

---

### Post by thegnu on 2010-10-23
you can turn off the switchable graphics in the bios.  i've had my t510 for about 2 weeks, and i'm triple booting linux/win/mac.  the optimus graphics only work in windows so far, but i haven't tried hard in linux.  what happens if you leave optimus on is it just brings you to a login terminal (where you'd have to login, then 'sudo reboot')

the 9-cell battery lasts for freaking ever in windows with optimus enabled, though!  pretty decent in linux, but i've only used linux with the always on nvidia, which eats into the battery life a fair amount.

i love this laptop.

---

