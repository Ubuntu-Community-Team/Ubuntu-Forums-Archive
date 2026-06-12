---
title: "better support to hardware with fairly lesser number of bugs"
date: 2008-11-09
forum: General Help
---

### Post by electronique on 2008-11-09
hello,

I have been using ubuntu 8.04 64bit for the last 3 months.
I have found it to be a really GOOD distro,
but the problem I have is that it seems that it 
has bug in feature controlling my laptop fan (the laptop temperatures usually remain > 50C the temps are not that high while using windows xp).
I tried a lot and at last gave up.

I want to ask if you know of a fairly bugless , easy enough (but I never had any trouble installing tarred files ..... just to give you an idea) and supporting my hardware and yes .... gnome please .I am even ready to use 32 bit version os.
I would get ubuntu 32 bit if you can assure me that I can control my fan by configuring it .
Mine is an acer 5920 
2gb RAM , 1.83 Ghz , mobile intel 965 express chipset family.

---

### Post by aikiwolfie on 2008-11-09
Have you installed powertop? If not open a terminal and enter the following:

```
sudo apt-get install powertop
```

Enter your password when prompted, let the install run it's course answering any prompts that appear. Next start up power top with;

```
sudo powertop
```

Again enter your password if prompted.

Powertop will now scan your system to find efficiency savings and try and make it run better. It won't change anything without asking you first. So it's completely safe.

It's also helpful to make sure you have the latest drivers for your graphics card and BIOS upgrades for your laptops motherboard. Dell have for example added code to their BIOS to make system fans kick in sooner to try and stop Nvidia GPUs from melting themselves.

Hope that helps.

---

### Post by electronique on 2008-11-10
thankyou for your reply.
but powertop does not show(i am not able to find out) a method to control my
fan speed.
and how do i find updates to my bios etc using it.

and it shows me a suggestion :
Suggestion: Disable 'hal' from polling your cdrom with:
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a

should i do that?

---

### Post by aikiwolfie on 2008-11-11
Hmm ... I'll have to get back to you on the fan problem. The CD-ROM thing isn't essential. It'll just save a little power and auto run might not work afterwards.

---

### Post by aikiwolfie on 2008-11-11
Have you tried adjusting the BIOS settings for the fan? Apparently they need to be set to "legacy". It seems some other distros work better with your Intel chipset.

[QUOTE=http://intellinuxgraphics.org/user.html]"In the BIOS settings, enter the page for "PC Health Status" and set "CPU Fan Control" to "legacy". If it is set to "INTEL (R) QST" then BIOS uses too many memory-type-and-range registers (MTRRs) and doesn't leave enough of them for X, and 3D performance will be about 1/5 normal."[/QUOTE]

[http://intellinuxgraphics.org/user.html]("http://intellinuxgraphics.org/user.html")

---

### Post by electronique on 2008-11-12
In the bios there is no entry for bios settings for fan.
I will try to find out if there is a later version of the bios( but mine is not an old laotop).
Is there any command or a way to find the mother board information
on my laptop.

God !, should I install any driver or something.

---

