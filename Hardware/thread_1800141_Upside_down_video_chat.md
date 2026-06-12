---
title: "Upside down video chat"
date: 2011-07-08
forum: Hardware
---

### Post by FLCL on 2011-07-08
I'm having an issue where in Google video chat I'm upside down.
Tried following this:

> **Halfling Rogue said:**
> I did it by changing the Launcher properties for Firefox [as per the instructions here]("http://radu.cotescu.com/flipped-images-ubuntu-webcam/").

Set up the .sh file following the directions in the link and then paste this in the Command box for the Firefox Launcher:

```
webcamWrapper.sh firefox %u
```

That'll run the webcam patch whenever you run Firefox, which should enable the flipping for all browser-related cam apps.

But when I launch Firefox from the icon now I get a "Failed to execute child process, webcamWrapper.sh (permissions denied)" the sh is in ~bin. Any help?

---

### Post by gordintoronto on 2011-07-08
If you right-click on a file from the Nautilus file manager, you can select "Properties," and one tab is Permissions.

If you open Accessories/Terminal and enter the command:
gksudo nautilus
you can change the permissions. Be very, very careful, a wrong click can really mess up your system.

If you run Cheese Webcam Booth, is your image upside down?

---

### Post by FLCL on 2011-07-21
Sorry, late reply. This is for Google talk video chat. I changed the file permissions using the method described and it opens fine now :)

---

