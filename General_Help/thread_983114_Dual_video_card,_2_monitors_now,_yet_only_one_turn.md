---
title: "Dual video card, 2 monitors now, yet only one turns on?"
date: 2008-11-15
forum: General Help
---

### Post by PsychedelicWonders on 2008-11-15
I just added a 2nd monitor to my dual video card.

It is a 19" Basic Dell flat screen monitor.

Everything has power, but right now the new one is black.

But it seems like its in sleep mode or something, no picture and the power button is orange/amber right now.

If I press the power button that is amber, it turns the monitor off completely.

If I turn the monitor back on, the green power button on the monitor and the blue power button on the attachable speaker come on and then go off after a couple of seconds and then the amber power light comes back on.

Do I have to enable it or something to get it to turn on because its a dual card?

---

### Post by PsychedelicWonders on 2008-11-15
anyone?

---

### Post by PsychedelicWonders on 2008-11-16
bump

---

### Post by PsychedelicWonders on 2008-11-16
bump

---

### Post by overdrank on 2008-11-16
> **PsychedelicWonders said:**
> bump

What is the model of the graphics card? If you are using Hardy 8.04 you can use the command ```
gksu displayconfig-gtk
``` to see if is detected there.

---

### Post by PsychedelicWonders on 2008-11-16
I have an Nvidia card.

I'm not at that particular computer right now, I will be in a couple of hours.

I've read something about Nvidia Settings manager or something, where is this actually at?

Is that where I would normally activate both screens?

---

### Post by overdrank on 2008-11-16
> **PsychedelicWonders said:**
> I have an Nvidia card.

I'm not at that particular computer right now, I will be in a couple of hours.

I've read something about Nvidia Settings manager or something, where is this actually at?

Is that where I would normally activate both screens?

You can use the command ```
gksu nvidia-settings
``` there  you can setup the second monitor.

---

### Post by PsychedelicWonders on 2008-11-16
ok will that bring up a pretty basic walk thru?

I'm not sure if I want the monitors to be "separate" or one big desktop.

Any yays or nays one way or another?

---

### Post by overdrank on 2008-11-16
This may help
[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)

---

### Post by PsychedelicWonders on 2008-11-16
will i need to download drivers for this setup?

---

### Post by overdrank on 2008-11-16
> **PsychedelicWonders said:**
> will i need to download drivers for this setup?

Well have you installed the drivers for your graphics card? If not then yes you will need to install the nvidia drivers and if you are using Hardy then also install nvidia-settings.

---

### Post by PsychedelicWonders on 2008-11-16
Ok I'm at home now and am working on the computer.

I tried installing the drivers via the "see BinaryDriverHowto/Nvidia for using the built in method, Hardware Drivers or Restricted Drivers Manager" route

I'm running into this problem...

If your card does not appear in this list of cards known by Ubuntu 8.04 NVIDIA binary drivers (e.g. the 9600 GT) then there is no Ubuntu 8.04 provided binary driver. For unsupported workarounds try the links in See Also.

I have the 9600 GT card and when I go to the next part it suggests, I get lost.

I clike on the "see also" and it kicks me to the bottom of the page and I dont know what to look at and read?

---

### Post by PsychedelicWonders on 2008-11-16
> **overdrank said:**
> Well have you installed the drivers for your graphics card? If not then yes you will need to install the nvidia drivers and if you are using Hardy then also install nvidia-settings.

I thought ubuntu never needed any drivers installed like windows?

How do I install the drivers for this card and how do I install the nvidia settings?

---

### Post by tuxxy on 2008-11-16
That card will require the v177 nVidia drivers as its a new model, these should be provided in system > admin > hardware drivers as you say, if not then you could try envyng-gtk to select and install the correct driver.

You could also download direct from nVidia website and try an install that way, either way that card should work with v177 drivers.

Once your drivers are installed you want to download nvidia-settings
```

sudo apt-get install nvidia-settings
```

Run nvidia-settings and select the **x server display configuration** tab, click configure to enable your twinview here, also there many options for configuring like relative position, overlapping etc

---

### Post by PsychedelicWonders on 2008-11-16
> if not then you could try envyng-gtk to select and install the correct driver.

Where do I do this exactly?

I tried in the terminal and add/remove programs and got nothing?

---

### Post by tuxxy on 2008-11-16
The package is called **envyng-gtk**, search for that in synaptic or try in terminal;

```
sudo apt-get install envyng-gtk
```

---

### Post by PsychedelicWonders on 2008-11-16
> **tuxxy said:**
> The package is called **envyng-gtk**, search for that in synaptic or try in terminal;

```
sudo apt-get install envyng-gtk
```

Ok, just ran that code, everything went normal, so that right there automatically installed the correct driver?

Or now do I have to go activate this driver i just downloaded?

Am I ready to run

```
sudo apt-get install nvidia-settings
```

---

### Post by PsychedelicWonders on 2008-11-16
will I actually notice a visual difference with anything with these new drivers installed?

---

### Post by PsychedelicWonders on 2008-11-16
just got this...

psychedelicwonders@JohnnyScience:~$ sudo apt-get install nvidia-settings
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
psychedelicwonders@JohnnyScience:~$ 


What do I do?

---

### Post by PsychedelicWonders on 2008-11-17
still havent figured it out.

---

### Post by TeXtonyx on 2008-11-17
I use separate. I might have a program that can manipulate digital
camera images open with a particular image selected. On the other
screen, I have them set up so that it's easy see both, I might
have a tutorial open that has steps about tweaking the image,
which I refer to back and forth between screens, tutorial/gimp.

So it depends on what use you will put monitors to. Try it both
ways, you can change it by running nvidia-settings again. I figure
there must be situations where both choices have some particular
advantage with each setting, which is why more than one is offered.

I've seen a lot of howto(s) for installing nvidia drivers. Downloading
the driver for your card from nvidia, apt-get install build-essential,
and using Envyng to install the driver. I read several of them by using
the Search window at the top of the forum window. Probably using the
search terms, nvidia and your model of nvidia card, will provide info 
about how somebody solved the problem of installing the correct driver
and the problems that were overcome. For instance mine was 
Geforce Fx 5500 (which is a dual monitor card).

---

### Post by PsychedelicWonders on 2008-11-17
> **TeXtonyx said:**
> I use separate. I might have a program that can manipulate digital
camera images open with a particular image selected. On the other
screen, I have them set up so that it's easy see both, I might
have a tutorial open that has steps about tweaking the image,
which I refer back and forth between.

So it depends on what use you will put monitors to. Try it both
ways, you can change it by running nvidia-settings again. I figure
there must be situations where both choices have some particular
advantage with each setting, which is why more than one is offered.

No I do like the way you do it.

Allows you to "work" on one screen and have the others there to assist you.

And obviously sometimes you may have to work in different resolutions or whatever so it would be better I think to make them separate.

You're right though, I'm sure there are pros and cons to each way though.

I'm interested to see how the 3-D doughnut (sphere) I have going on and how that feature will work on 2 screens.

But first I gotta get past my last post because I'm stuck there still.

---

### Post by PsychedelicWonders on 2008-11-17
> **PsychedelicWonders said:**
> just got this...

psychedelicwonders@JohnnyScience:~$ sudo apt-get install nvidia-settings
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
psychedelicwonders@JohnnyScience:~$ 


What do I do?

still stuck on this problem

---

### Post by PsychedelicWonders on 2008-11-17
bump

---

