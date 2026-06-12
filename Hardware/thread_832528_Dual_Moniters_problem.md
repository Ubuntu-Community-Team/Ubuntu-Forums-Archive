---
title: "Dual Moniters problem"
date: 2008-06-17
forum: Hardware
---

### Post by but2002 on 2008-06-17
I have two graphics cards, one is an NVIDIA GeForce 6200 128MB AGP, and the other card is an NVIDIA GeForce FX 5500 256 MB PCI

Right now, they are set to Seperate X Screens, and they seem to work independantly of each other, almost as if i'm on two seperate computers.  How would I go about making them work like in Windows, where you can just drag from one to the other?

Second.  I had Emerald installed, and when I enabled the second screen, my windows are left borderless, (With Compiz Fusion running) so I uninstalled Emerald, and started MetaCity and then tried to reload Compiz, I'm still borderless!
What do I do?

So, basically, I want to have Compiz Fusion with Emerald working right, as well as two seperate screens, that don't act like two seperate computers.

Thanks!

---

### Post by ad_267 on 2008-06-17
I'm not sure about how this works with two video cards as I have my two monitors set up on one card but this worked for me:

Run "sudo nvidia-settings" and enable the second monitor with the "twinview" option and set that up then save the settings to the xorg.conf file.

To get your window borders with compiz back try running these by pressing alt-f2 then run "compiz --replace && emerald --replace"

---

### Post by but2002 on 2008-06-17
TwinView is disabled, and unclickable.  Allright, I'll give the emerald thing a try

Nope, my windows are still borderless.

Allright, how would I get compiz to use Metacity's decorator?

---

### Post by ad_267 on 2008-06-17
Edit: Sorry wrong info. Its alt-f2 and "gtk-window-decorator --replace"

I'm not sure why you can't drag between the monitors. Even using separate X screens I'm able to do this. I guess it has to do with using two video cards.

You can permanently set the window decorator in the compizconfig-settings-manager under the window decorations plugin.

---

### Post by but2002 on 2008-06-18
Allright, I will set it to GTK when I get back under my Ubuntu install, right now I'm under Windows

If anyone else has an idea why I can't do that, please let me know!

Thanks!

EDIT: OH!

Does it have anything to do with the fact the moniters aren't lined up?  I have one slightly higher than the other, so I set it that way in the config.

---

### Post by jonatan5 on 2008-06-18
I just enabled my second monitor at system settings resolution, unchecked clone displays and I got two monitors on who i could drag objects.  BUT it only worked with second monitor being under first, so like you go down to get into it. I moved second monitor to side or top place, clicked OK, but it jumped back to being under.

---

### Post by but2002 on 2008-06-19
I managed to get it to work now, but now Compiz won't work, with both of them.

Does anyone know a solution to this issue now?

---

### Post by ad_267 on 2008-06-19
You can't use compiz unless you're using twinview I found. So I guess you're out of luck unless someone else knows better.

---

### Post by but2002 on 2008-07-06
I did some reading elsewhere, and I found it is impossible to use Compiz across multiple moniters when they are on seperate video cards.

I'm extremely dissapointed :(

---

