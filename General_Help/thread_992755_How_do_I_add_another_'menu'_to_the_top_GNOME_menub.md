---
title: "How do I add another 'menu' to the top GNOME menubar?  New one near Applications..."
date: 2008-11-25
forum: General Help
---

### Post by Panarchy on 2008-11-25
Hello

Using Ubuntu 8.10, x86.

How do I make my own custom 'menu-list'? 

Currently there are 3, Applications | Places | System 

I would like to add a fourth one, but I don't know how!

So, **how do I add a fourth one? **

Please reply,

Thanks in advance,

Panarchy

---

### Post by ibutho on 2008-11-25
I think the menubar is some sort of applet, so if you don't get an answer here, ask in the GNOME mailing lists. If you are a developer, look at the source code for gnome-applets and hopefully you will get some hints about what you are supposed to do.

---

### Post by wizard10000 on 2008-11-25
> **Panarchy said:**
> So, **how do I add a fourth one? **

Right-click the icon to the left of the menus and select "Edit Menus".

:)

---

### Post by DieB on 2008-11-25
if you are no developer, probably the option of adding a drwaer to the Panel will do the trick for you?

---

### Post by Panarchy on 2008-11-25
> **DieB said:**
> if you are no developer, probably the option of adding a drwaer to the Panel will do the trick for you?

That's the second or third time that's been suggested to me. How do I do that?

> **ibutho said:**
> I think the menubar is some sort of applet, so if you don't get an answer here, ask in the GNOME mailing lists. If you are a developer, look at the source code for gnome-applets and hopefully you will get some hints about what you are supposed to do.

I asked on there IRC channel, and they also said something about an applet. Can you please direct me in the direction of where I may be able to find such an applet?

But they said that if I wanted to find what part of the source-code it is from, for me to try editing the gnome-panel source code.

If I were to do that (learning curve!), how would I re-encorporate it back into Ubuntu 8.10?

Please reply

Thanks in advance,

Panarchy

---

### Post by jenkinbr on 2008-11-25
To do a drawer, Right-click an empty spot on the panel and click 'add to panel'

in the search box, type 'drawer'
--or--
scroll down the list until you find the drawer

drag the drawer entry to where you want it on the panel.

Next you will need to popluate the menu by going through the menu, find the items you want in the menu, and right-click on them and add them to your panel.  You can then drag them (or right-click > move them) into the drawer.

hope this helps. (note: you will not get the text next to the entries)

---

### Post by whitethorn on 2008-11-25
You could also create a new folder under Applications/Places/System.  To do that you have to right click on Applications -> Edit Menus   Then click on one of the left Menus to choose where you want to add yours to.  Then click on New Menu, call it how you want, now you should get somethign that looks like a folder, and in there you can add whatever entries you like.

---

### Post by SeanHodges on 2008-11-25
> **Panarchy said:**
> I asked on there IRC channel, and they also said something about an applet. Can you please direct me in the direction of where I may be able to find such an applet?

But they said that if I wanted to find what part of the source-code it is from, for me to try editing the gnome-panel source code.

If I were to do that (learning curve!), how would I re-encorporate it back into Ubuntu 8.10?

Editing the source code will require fair a bit of patience and perseverance, so make sure you're willing to learn before taking it on...

The package you will need to modify is called "gnome-main-menu", you can get it using:

```
apt-get source gnome-main-menu
```

As a start, you could try drawing a new menu item in the applet UI, which I believe is the "slab-window" glade file (easiest way to modify this is using the glade-3 program):

main-menu/src/slab-window.glade

No doubt there will be a fair bit of coding needed to actually bind this to a sub-menu in the config, but you'll need to dig in and ask around when you start getting stuck. Be sure to read this as well: [https://wiki.ubuntu.com/UbuntuDevelopment](https://wiki.ubuntu.com/UbuntuDevelopment)

If you are not a programmer, you will need to learn how to program first (which will take time). In that case, it might be worth posting an idea on the Brainstorm site ([http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)) in case someone else is interested in taking on the project, or in assisting you.

---

### Post by Panarchy on 2008-11-25
^Thanks... didn't know of the source command.

I will give it a go.

Which compiler should I use?

Also, I really would like to take on this project, and no, I'm not much of a programmer, but a learning curve still has 'learning' in it! :lolflag:

So from what you've written, it seems that if I just edit that, I don't need to manually download GNOME?

Also, how would I go about reencorpotating the code I add back into GNOME, then back into Ubuntu?

Please reply

Thanks in advance,

Panarchy

PS: You mentioned gnome-main-menu, I thought that gnome-panel was the one I was looking for? :confused:

> **whitethorn said:**
> You could also create a new folder under Applications/Places/System.  To do that you have to right click on Applications -> Edit Menus   Then click on one of the left Menus to choose where you want to add yours to.  Then click on New Menu, call it how you want, now you should get somethign that looks like a folder, and in there you can add whatever entries you like.

Ah... nah, doesn't look that great... doesn't really stand out the way I want it to.

---

### Post by SeanHodges on 2008-11-26
> **Panarchy said:**
> Which compiler should I use?

Bear in mind that I don't contribute in the development of the main menu applet, you'll need to read the README file (and possibly the INSTALL file as well) in the source code directory to find out how to track down these kind of questions.

> **Panarchy said:**
> So from what you've written, it seems that if I just edit that, I don't need to manually download GNOME?

No, what I've written is just a starting point to get you going. You'll need to liaise with the developers to find out what else you'll need. Often you can just make some changes to the source and use a tool like [pbuilder]("https://help.ubuntu.com/ubuntu/packagingguide/C/gs-pbuilder.html") to build everything for you.

> **Panarchy said:**
> Also, how would I go about reencorpotating the code I add back into GNOME, then back into Ubuntu?

I'm not sure this particular project is something you will want to contribute back to Ubuntu - unless everyone is going to want this fourth item in the main menu applet? Perhaps you are planning to make the number of menus customisable, which would be the project much more complicated, I recommend you stick to something simple for now.

As I said before, contributing code back to the community is explained in the wiki: [https://wiki.ubuntu.com/UbuntuDevelopment](https://wiki.ubuntu.com/UbuntuDevelopment).

> **Panarchy said:**
> PS: You mentioned gnome-main-menu, I thought that gnome-panel was the one I was looking for? :confused:

Apt-get the gnome-panel source if you want and have a look. It contains the source code for a whole load of applets that are available to the panel, but not the main menu that is installed by default in Ubuntu. This is provided in "gnome-main-menu".

---

### Post by Panarchy on 2008-11-26
> **SeanHodges said:**
> Bear in mind that I don't contribute in the development of the main menu applet, you'll need to read the README file (and possibly the INSTALL file as well) in the source code directory to find out how to track down these kind of questions.


Okay, thanks... I'll also have a look at the GNOME IRC channel.

> **SeanHodges said:**
> No, what I've written is just a starting point to get you going. You'll need to liaise with the developers to find out what else you'll need. Often you can just make some changes to the source and use a tool like [pbuilder]("https://help.ubuntu.com/ubuntu/packagingguide/C/gs-pbuilder.html") to build everything for you.

Okay, thanks

> **SeanHodges said:**
> I'm not sure this particular project is something you will want to contribute back to Ubuntu - unless everyone is going to want this fourth item in the main menu applet? Perhaps you are planning to make the number of menus customisable, which would be the project much more complicated, I recommend you stick to something simple for now.

That complicated project sounds very interesting! But I think I'll have enough trouble getting this to work. Maybe sometime in the future I will make that tool?

Also, I think I wrote down the wrong thing (that gave the wrong idea across). What I wish to do is NOT to put what I add back into the official ubuntu iso, but into a custom ubuntu iso that I am creating. 

How would I go about doing that?

> **SeanHodges said:**
> As I said before, contributing code back to the community is explained in the wiki: [url]https://wiki.ubuntu.com/UbuntuDevelopment[/url

What I wish to do is NOT to put what I add back into the official ubuntu iso, but into a custom ubuntu iso that I am creating.

How would I go about doing this?

> **SeanHodges said:**
> Apt-get the gnome-panel source if you want and have a look. It contains the source code for a whole load of applets that are available to the panel, but not the main menu that is installed by default in Ubuntu. This is provided in "gnome-main-menu".

Ah... okay!

Thanks for all your help.

And please answer the (extra) questions I have just asked.

Thanks in advance,

Panarchy

---

### Post by SeanHodges on 2008-11-27
> **Panarchy said:**
> I think I wrote down the wrong thing (that gave the wrong idea across). What I wish to do is NOT to put what I add back into the official ubuntu iso, but into a custom ubuntu iso that I am creating. 

Ah OK no problem.

I haven't built a custom Ubuntu CD myself (although it would be an interesting project, I intend to try sometime), the best way to find information on tasks like this is usually to start by searching the Ubuntu Wiki. My quick search has brought up 2 alternatives:

Building custom install ISO's: [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

Building custom live CD's: [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

I imagine you want to do the first one, but they're both worth a look. Be sure to update the Wiki instructions if they need it, as I'll probably have a read of them in the near future ;)

---

### Post by Panarchy on 2008-11-28
Thanks for your reply.

Please also tell me how I can reincorporate what changes I did to the GNOME interface back into my custom Ubuntu ISO.

Thanks in advance

Panarchy

---

### Post by SeanHodges on 2008-11-28
> **Panarchy said:**
> Thanks for your reply.

Please also tell me how I can reincorporate what changes I did to the GNOME interface back into my custom Ubuntu ISO.

Thanks in advance

Panarchy

That I don't know. As I said I have not created a custom ISO before.

---

### Post by Panarchy on 2008-11-29
^Thanks anyways.

*Calling all members of this forum*!!!

Can someone please tell me how, once I've made changes to the gnome source code, I can 'put it back' into a Custom Ubuntu LiveCD?

Thanks in advance,

Panarchy

---

### Post by jenkinbr on 2008-12-01
> **Panarchy said:**
> ^Thanks anyways.

*Calling all members of this forum*!!!

Can someone please tell me how, once I've made changes to the gnome source code, I can 'put it back' into a Custom Ubuntu LiveCD?

Thanks in advance,

Panarchy
That's no easy task, but I think this wiki article should help.  I stumbled on it a while ago while thinking about making my own liveCD for doing full-system backups, but have never tried it.
url: [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

This may also be of use: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

I know very little about this, but hopefully this will help you.

---

### Post by Panarchy on 2008-12-02
> **jenkinbr said:**
> That's no easy task, but I think this wiki article should help.  I stumbled on it a while ago while thinking about making my own liveCD for doing full-system backups, but have never tried it.
url: [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

This may also be of use: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

I know very little about this, but hopefully this will help you.

Ah... thanks. Sorry, but both URLs have already been suggested to me.

Unfortunately neither helped :(

Please recommend a way of doing what it is I would like to do.

Thanks in advance,

Panarchy

---

### Post by 3rdalbum on 2008-12-02
*Sorry for the double-post.*

---

### Post by 3rdalbum on 2008-12-02
At what stage are you at for your custom ISO? Have you decompressed the squashfs filesystem onto your hard drive?

If you have done this already, then you need to copy the modified source code into the decompressed filesystem (just drag and drop with the middle mouse button/scroll wheel held down). Go into a terminal and do the following:

```
sudo chroot 
```

and before pressing the Enter key, drag the folder containing the uncompressed filesystem to the terminal. Now press the Enter key. The concept is difficult to explain, but any program running inside this terminal window from now on, will only see the contents of the uncompressed filesystem. It's like you're running your custom CD.

Compile the source of the Gnome main menu or whatever applet it is that you modified. It will be installed into the uncompressed filesystem rather than into your real Ubuntu installation. Recompress the filesystem as normal and create your ISO, and the modified applet will be there.

If you have not uncompressed the squashfs filesystem, then you need to look at the HOWTO for live CD customisation.

---

### Post by Panarchy on 2008-12-04
> **3rdalbum said:**
> At what stage are you at for your custom ISO? Have you decompressed the squashfs filesystem onto your hard drive?

If you have done this already, then you need to copy the modified source code into the decompressed filesystem (just drag and drop with the middle mouse button/scroll wheel held down). Go into a terminal and do the following:

```
sudo chroot 
```

and before pressing the Enter key, drag the folder containing the uncompressed filesystem to the terminal. Now press the Enter key. The concept is difficult to explain, but any program running inside this terminal window from now on, will only see the contents of the uncompressed filesystem. It's like you're running your custom CD.

Compile the source of the Gnome main menu or whatever applet it is that you modified. It will be installed into the uncompressed filesystem rather than into your real Ubuntu installation. Recompress the filesystem as normal and create your ISO, and the modified applet will be there.

If you have not uncompressed the squashfs filesystem, then you need to look at the HOWTO for live CD customisation.

Thanks, most helpful advice so far!

I'll give it a go!

Thanks!

Panarchy

PS: Do you know of a version of Ubuntu that's been stripped down... like no translations, no un-needed programs (eg OpenOffice), no documentation... one that contains only, like the menus, gedit, terminal, GNOME, apt (and other debian dependencies)?

If you know of one, please tell me (will make it easier to add what I want, because when I try myself, it keeps deleting things I don't want it to delete, and ends up stuffing my LiveCD...

---

### Post by jenkinbr on 2008-12-05
I would use the alternate install CD to install a Command-line only system, then build up on that, leaving out the extra, unnecessary stuff.

You'll want to then use apt to add things like the Xorg server and Gnome

---

### Post by Panarchy on 2008-12-08
Hmm... not to bad an idea, I may give it a go.

---

