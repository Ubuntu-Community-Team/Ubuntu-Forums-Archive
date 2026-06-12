---
title: "how do i setup xdmcp server/display forward on linux (beagleboard) ?"
date: 2008-11-14
forum: General Help
---

### Post by montamer on 2008-11-14
Hi

I got my beagleboard recently. I dont have a dvi-d lcd as of now. So want to remote login into it from my ubuntu pc.
I can connect both of them through net

What are things i need to install in beagleboard so that i will be able to do xdmcp login into beagleboard linux (minimal stuff no gnome desktop).
I did a bit of google and found something called xdm. I installed it on beagle and tried to login through xdmcp from ubuntu but im getting a blank screen.

or is there some way i can forward the display of beagleboard to ubuntu pc ? and display in a window.

thanx in advance

---

### Post by locutus42 on 2008-11-16
that's going to be tough for two reasons. One, you've not done this before with a standard system which had a GUI display to work with and secondly, you'll be flying blind on the beagleboard trying to set this up.

Maybe it would be a good step to first get ssh running and get that running so you are using xforwarding to run X apps remotely. Once there, you might be able to setup something like x11vnc to then get the beagleboard desktop remotely.

Another option would be to install ubuntu into a virtual machine and work with getting that configured to use either x11vnc or xdmcp before attempting to do it blind on the beagleboard. Just throwing out ideas for you instead of waiting for someone else to post step-by-step instructions for you.

---

