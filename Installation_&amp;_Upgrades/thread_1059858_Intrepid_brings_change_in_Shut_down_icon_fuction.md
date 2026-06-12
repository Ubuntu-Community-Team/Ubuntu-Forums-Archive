---
title: "Intrepid brings change in Shut down icon fuction"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by Handssolow on 2009-02-04
Today's upgrade to Intrepid on my wife's PC has changed the function of the top panel's red+white Shut Down icon instead it's a "log out of session" dialogue window with only two choices, "Log Out" or "Switch User". There's no switch down option neither is there a guest log in option. I can find a grey shut down icon under System but I'd like to configure this PC similar to my own Intrepid PC with a full list of options available from the red icon.

By the way, in Hardware Drivers I've also not been able to activate the ATI/AMD proprietary FGLX graphic driver that's being shown as an option. It goes through the motions of installing the new driver but still shows it as not activated. Where's this driver hiding?

---

### Post by apunc1 on 2009-05-10
did you ever figure this out? the same thing happened to me too: two Jaunty installs, one left  the shutdown function in the upper right and one did not.
thanks.

---

### Post by Handssolow on 2009-05-12
There was no change to my wife's PC after the upgrade to 9.04, the top right corner red button opens a window but still doesn't have either a Guest Session option or Shut Down only Log Off and possibly the hibernate option from my memory. I've not looked if she's got the default gdm-guest-session package installed like I have on my PC.

The working solution for her was to edit the top toolbar menu and add the grey shut down icon which opens a window with several options including Shut Down but still no guest session option. Before this, Shut Down was only available at the bottom of the System window.

(I edited with a right click over Applications>Edit Menus)

---

### Post by Handssolow on 2009-05-14
I've made some progress. The guest account option is back on my wife's PC with a right click at the top for "Add to Panel" and selecting User Switcher (applet available in Ubuntu at least). The puts up her user name and a smaller second red login icon which opens a window with the guest and shut down options. The larger red square icon options gives only log out and switch user unlike on my own PC which has more options like guest account and shut down.

My interpretation being that somehow during the upgrade to Intrepid the Log out icon became just that and lost its association with the user switcher applet. Her PC's upgrade to JJ didn't bring the guest account option by default either.

---

