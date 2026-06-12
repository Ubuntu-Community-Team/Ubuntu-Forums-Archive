---
title: "Panel error message"
date: 2008-11-05
forum: General Help
---

### Post by RonB123123 on 2008-11-05
When I right click on my top gnome panel and click on Properties, it brings up the window and an error message.

The folder contents could not be displayed
Error stating file '/tmp/evince-6347': No such file or directory

After closing the error window, it says in the properties window:
Some of these properties are locked down

Screen shot:
[img]http://img354.imageshack.us/img354/2816/panelpropertieserror2hx6.png[/img]

I'm using the new Intrepid 8.10 Ubuntu.

---

### Post by RonB123123 on 2008-11-06
bumping... is there any way to fix this?

---

### Post by EXCiD3 on 2008-11-06
Does this continue if you reboot?

---

### Post by RonB123123 on 2008-11-06
Yeah it does, but after doing updates, it still shows the Error window but it does not say "Some of these properties are locked down" in the Properties window.

---

### Post by EXCiD3 on 2008-11-06
did you ever do a dist upgrade? almost sounds like the new unlock feature on those dialogs has caused the problem. unfortunately i dont know of any way to fix that. :(

---

### Post by RonB123123 on 2008-11-08
yeaah i did a distribution upgrade from 8.04. 
The "Some of these properties are locked down" message is back. Hopefully someone will fix it then. :(

---

### Post by PrimitiveSix on 2008-12-04
i have the same problem...i have ubuntu 8.10 ...can somebody help me ?

---

### Post by coolguybri79 on 2009-01-04
> **RonB123123 said:**
> When I right click on my top gnome panel and click on Properties, it brings up the window and an error message.

The folder contents could not be displayed
Error stating file '/tmp/evince-6347': No such file or directory

After closing the error window, it says in the properties window:
Some of these properties are locked down

Screen shot:
[img]http://img354.imageshack.us/img354/2816/panelpropertieserror2hx6.png[/img]

I'm using the new Intrepid 8.10 Ubuntu.

Ok here's how you fix this...

[applications] > [system tools] > [configuration editor]
(if you don't see configuration editor then you need to go to "main menu" in [system preferences]

in configuration editor, expand [aps], [panel], [toplevels]... 
check the "image" property on the right for the file that is displayed in the error message. it is in either panel_0, or top_panel_screen0 on the left side. just delete the path and filename in the image property field

hope this helps!

---

### Post by RonB123123 on 2009-02-16
thanks coolguy. The annoying evince error is gone but it still says "Some of these properties are locked down." Is there a way to fix that?

---

### Post by Poor Wandering One on 2009-02-17
I'm having the same issue. How to unlock a panel so that it can be moved.
Any ideas out there?

---

### Post by RonB123123 on 2009-02-20
After following what coolguy said, a reboot, and updates, I am no longer having this problem. Use gconf-editor if you can't find it.

---

### Post by RonB123123 on 2009-02-25
Strange, now my lower panel is experiencing the same problem. I dont get the prompt but I get the error message "Some of these properties are locked down"

I followed coolguys tip through gconf-editor and the image attribute was already empty. Any way to fix this?

---

### Post by achilleas.k on 2009-03-12
Well I think I know what's going on since I got the same problem. Someone who understands this better should correct me if I'm wrong.

I dragged an image onto the panel at some point which effectively changed the panel background to the image. Since the image wasn't saved anywhere it was just an image in the /tmp directory, so after a reboot the file in the /tmp directory was gone. Now the panel wasn't set to have the image as background but every time I opened the properties it would look for it since it was supposed to appear in the options.
I followed coolguy's instructions and I got it resolved. I'm assuming that it can also be resolved by opening the panel properties, switching to the background tab, select background image, browse for a background image, select an image you keep anywhere and then just switch back to "None (use system theme)" option. That way, every time you open the properties, it won't have trouble finding the image path you have saved for the "Background image" option.

Now as for "Some of the properties are locked down" isn't an error but a simple warning or just a bit of information. The reason you get it is because you have the panel locked. To unlock it just right click directly on the panel and click "Allow panel to be moved". This enables you to change the orientation of the panel (e.g. from bottom to side panel).

---

