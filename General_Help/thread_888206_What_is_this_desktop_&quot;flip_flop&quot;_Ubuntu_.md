---
title: "What is this desktop &quot;flip flop&quot; Ubuntu does?"
date: 2008-08-12
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-12
What is this "flip flop" that occurs when I scroll my mouse button or I hit that little icon in the lower right?

---

### Post by sandysandy on 2008-08-12
its one of ur other desktops. ubuntu supports multiple desktops.

---

### Post by tamoneya on 2008-08-12
they are called workspaces.  It allows you to have apps open in separate windows and you can switch back and forth.  That way you dont just have piles of things.  You could for example have firefox in one and Open Office in another.

---

### Post by PsychedelicWonders on 2008-08-12
Hmm.  interesting.

Kind of a "virtual machine" to a certain degree? but more so for programs?

Is there any way to turn it on and off?

---

### Post by shazbut on 2008-08-12
Right click on the workspaces next to the trash, and choose preferences. You can assign more or less rows and columns.  I usually have 5 columns, because i can ;).
You can move between workspaces using ctrl-alt-[arrow], or use ctrl-alt-shift-[arrow] to take the active window to the new workspace.

---

### Post by SunnyRabbiera on 2008-08-12
> **PsychedelicWonders said:**
> Hmm.  interesting.

Kind of a "virtual machine" to a certain degree? but more so for programs?

Is there any way to turn it on and off?


Yes the virtual desktop is sort of like a VM, as each virtual desktop is self contained though still apart of the same system.
And yes you can turn it off by limiting yourself to one desktop by changing the number of workspaces to 1

---

### Post by tamoneya on 2008-08-12
I wouldnt call it a VM because it isnt a machine (that is the M in VM).  Also in VMs you can move applications between machines.  This is possible with workspaces.  As for disabling do as mentioned above and set it to one workspace.  Then I would also recommend that you right click on the switcher applet in the bottom right and select remove from panel so that you dont have to see it.

---

### Post by Master Chief on 2008-08-12
More like virtual screens, but every workspace contains the same desktop, the same panels, and the same menus.

You can right-click on the applet and select "Preferences" and set "Columns" in the Workspace Switcher Preferences to 1, or any number you like.

---

### Post by jayson.rowe on 2008-08-12
I would say to think of it as "virtual monitors" rather than "virtual machines".

Seperate workspaces can make your work far more organized - they just take some getting used to if you've never used them before. Once you do, you'll love 'em.

---

### Post by PsychedelicWonders on 2008-08-12
> **tamoneya said:**
> I wouldnt call it a VM because it isnt a machine (that is the M in VM).  Also in VMs you can move applications between machines.  This is possible with workspaces.  As for disabling do as mentioned above and set it to one workspace.  Then I would also recommend that you right click on the switcher applet in the bottom right and select remove from panel so that you dont have to see it.

If I do shut it off in this manner, but I want to turn it back on later if I decide I want to use it, how or where do I do so?

I'm not sure I prefer the flip flopping to simply just clicking the tool bar below.  I'll have to think about it.

---

### Post by mb_webguy on 2008-08-12
If you remove the switcher applet, you can always put it back later by right clicking on the panel, selecting "Add to panel", and picking the Workspace Switcher.

---

### Post by PsychedelicWonders on 2008-08-12
sweet, got it all, easy enough!

thanks guys.

---

### Post by mrsteveman1 on 2008-08-12
Do not be alarmed, your machine is practicing to run for president some day.

---

### Post by tamoneya on 2008-08-12
> **mrsteveman1 said:**
> do not be alarmed, your machine is practicing to run for president some day.

+1

---

### Post by PsychedelicWonders on 2008-08-13
can you set different backgrounds on the different virtual workspaces?

---

### Post by mb_webguy on 2008-08-13
> **PsychedelicWonders said:**
> can you set different backgrounds on the different virtual workspaces?

If you're using Kubuntu, then yes, since KDE supports different wallpapers on different workspaces.

Gnome (used by Ubuntu) doesn't support different wallpapers on different workspaces, but you can do it anyway using Compiz-Fusion.  Install the Compiz-Fusion settings manager (which will show up as "Advanced Desktop Effects Settings" in your Preferences menu) by typing "sudo apt-get install compizconfig-settings-manager emerald" in the terminal.

Once you have the Compiz-Fusion settings manager installed, follow the instructions on [this page]("http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/").

The downside is you won't have any icons on your desktop, but you *will* have have different wallpapers...

---

### Post by PsychedelicWonders on 2008-08-13
what advantages are there in using Kubuntu over Ubuntu?

you said my desktop wont have icons, which Im fine with because I am actually running a MAC OS dock to keep all my icons on...

Will this dock be visable on all of the workstations with my icons, yet giving me different backgrounds?

---

### Post by mb_webguy on 2008-08-14
The differences between Ubuntu and Kubuntu are that Ubuntu uses the Gnome desktop manager while Kubuntu uses the KDE desktop manager, and that they come with different applications.  

Gnome and KDE both do the same thing -- provide you with a desktop with windows, icons, menus and such -- they do it differently and provide different options and a different look.  It's really personal preference which is better.

While applications designed for Gnome will work on KDE and vice-versa, they need additional libraries that are part of their native desktop manager.  So to keep the size of the installation down, Ubuntu and Kubuntu use programs native to the desktop manager being used.  While Ubuntu uses Rhythmbox, Brasero, and Nautilus, for example, Kubuntu uses Amarok, K3b and Konqueror.

There's really no advantage to using either Ubuntu or Kubuntu.  It just depends on which desktop manager and which applications you prefer.  And at the end of the day, it really doesn't matter.  Both use the same repositories, and you can install any of the applications for one (including the desktop manager) on the other.  I use Amarok in Ubuntu, for example, because I like it better than Rhythmbox, but prefer the Gnome desktop manager and the other programs that come with Ubuntu.

---

### Post by PsychedelicWonders on 2008-08-14
hmm alright, thanks for that insight.

but you also said my desktop wont have icons, which Im fine with because I am actually running a MAC OS dock to keep all my icons on...

Will this dock be visable on all of the workstations with my icons, yet giving me different backgrounds?

---

### Post by zuner2012 on 2008-08-14
If you download compiz-fusion, set up the whole 3d cube thing, you will have no problem getting used to it. If you already have it installed, enable the 3d cube effect, the rotation effect, and some other effects. This is what makes multiple desktops fun.

---

### Post by PsychedelicWonders on 2008-08-14
> **zuner2012 said:**
> If you download compiz-fusion, set up the whole 3d cube thing, you will have no problem getting used to it. If you already have it installed, enable the 3d cube effect, the rotation effect, and some other effects. This is what makes multiple desktops fun.


What does the 3D cube thing do for this dock and multiple virtual monitors situation?

---

### Post by tamoneya on 2008-08-14
a video does much better than words in this case.

[http://www.youtube.com/results?search_query=3d+cube&search_type=](http://www.youtube.com/results?search_query=3d+cube&search_type=)

---

### Post by LeetSpeak on 2008-08-15
> **PsychedelicWonders said:**
> What does the 3D cube thing do for this dock and multiple virtual monitors situation?

Well one, to use the 3D cube, you need to have 4 workspaces. 2 workspaces = the Flip flop or w/e you were calling it. All the 3D cube does, is basically what it says, watch the link above me to see how it looks, but it's just a 3D cube lol. 

And as for your other question asking if your docks will still be showing, i'm not sure myself as i've just started using Ubuntu but, I'm pretty positive that they will stay, because I use the 3D cube right now, and the dock stays the same with the same icons, I don't think changing a picture on the desktop will effect the dock.

---

