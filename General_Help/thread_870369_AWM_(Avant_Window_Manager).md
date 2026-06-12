---
title: "AWM (Avant Window Manager)"
date: 2008-07-25
forum: General Help
---

### Post by PCessna on 2008-07-25
Hey all, Saw the dock, and just had to have it, Followed installiton instructions

```
sudo apt-get install avant-window-navigator
```

Type password, installs. Problem? Yes.

When trying to open this.. What seems to look wonderful dock the following happens

Top Left Corner or screen, a white box about the size of a cookie on this 17" wide-screen monitor, and at bottom an outline where dock should be, stays filled in white for about close to a half a second, and completely terminates. 

I'm not sure why. It's for Ubuntu 8.xx+

Any help? I have 8.04 LTS :)

Thanks 
-PCessna

---

### Post by damis648 on 2008-07-25
What is the terminal output of
```
avant-window-navigator
```?

---

### Post by PCessna on 2008-07-25
> **damis648 said:**
> What is the terminal output of
```
avant-window-navigator
```?
Misunderstood.. one second

---

### Post by damis648 on 2008-07-25
Omitted.

---

### Post by PCessna on 2008-07-25
> **PCessna said:**
> Misunderstood.. one second

Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

---

### Post by damis648 on 2008-07-25
Ah. You have to be be using a compositing window manager for AWN to work, IE compiz. Try System>Preferences>Appearance and the "Desktop Effects" tab. Try enabling it there. If it doesn't work, try System>Administration>Hardware Drivers and make sure your Graphics driver is installed.

---

### Post by PCessna on 2008-07-25
No drivers installed. I have a NVIDIA 7500 LE with 128MB ram, not sure of driver or how to enable

---

### Post by damis648 on 2008-07-25
System>Administration>Hardware Drivers and check the box next to your card.

---

### Post by PCessna on 2008-07-25
> **damis648 said:**
> System>Administration>Hardware Drivers and check the box next to your card.
No such thing, only device drivers, no box to check. (Nothing under device drivers)

---

### Post by tjwoosta on 2008-07-25
im pretty sure that in order to make awn function properly you will have to have compiz enabled

(system-preferences-appearance)   then click the visual effects tab and click extra


EDIT: sorry i just now read the post above that said the exact same thing i did

---

### Post by PCessna on 2008-07-25
Didn't I say it didn't work above man? :/

Any other docks, God dang, I just want a dock :{ 

Anyone have suggestions? Comon on Windows and Mac you don't need
no compositing software for a frigging dock.

---

### Post by damis648 on 2008-07-25
> **PCessna said:**
> Didn't I say it didn't work above man? :/

Any other docks, God dang, I just want a dock :{ 

Anyone have suggestions? Comon on Windows and Mac you don't need
no compositing software for a frigging dock.

Mac you do. They have a compositing window manager. Anyway, if you connot get compiz to work you might want to try cairo-dock.

---

### Post by tjwoosta on 2008-07-25
i think kiba dock will also work without compiz

---

### Post by damis648 on 2008-07-25
> **tjwoosta said:**
> i think kiba dock will also work without compiz

True, but it is a resource hog.

---

### Post by PCessna on 2008-07-25
> **damis648 said:**
> Mac you do. They have a compositing window manager. Anyway, if you connot get compiz to work you might want to try cairo-dock.

Cario dock has a nice black rectangular graphics-flasher around it. I call Cario Dock, Flashy-Graph. Why? it's a failure on my computer :-)

I'll try that resource hog and see if it's a resource hog too much for me, if not, then keep googling. 

Most docks are resource hogs, Macintosh is the best OS built for the Dock, IMO.

---

### Post by LIGC on 2008-07-25
you can enable composite in metacity too, try ```
gconftool-2 –set –type=bool /apps/metacity/general/compositing_manager true
```

---

### Post by moonbeam on 2008-07-25
For reference any compositor will more or less work with awn.

New versions of xfwm4 or metacity should be fine.  You just needed to enable the compositor in these WMs.

xcompmgr is also adequate.

of course compiz is fine but it could be viewed as overkill for something like awn :-)

some people also find cairo compmgr works.  Though that is really a YMMV situation.

---

### Post by overdrank on 2008-07-25
Moved :)

---

### Post by Darkade on 2008-07-25
> **PCessna said:**
> No such thing, only device drivers, no box to check. (Nothing under device drivers)

Install [Envy]("http://albertomilone.com/nvidia_scripts1.html") and see if you can get your Graphics card to work.

Envy will download the proper driver and install it, then you can enable Desktop Effects ie Compiz and then you will be able to use AWN

---

### Post by djrosen on 2008-07-25
System / Administration / Hardware Drivers - Do you have this enabled for your card?

---

