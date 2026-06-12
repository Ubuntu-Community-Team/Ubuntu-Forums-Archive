---
title: "[SOLVED] Apps in Main Menu"
date: 2008-10-20
forum: General Help
---

### Post by GrumpyGrenade on 2008-10-20
I just downloaded an app from the internet and now the only way to run in is to open the folder on my desktop and click the icon. I was wondering how I would go about to put the icon in the main menu so it is easy to access.

---

### Post by zephyrcat on 2008-10-20
Could you tell us what the app is or at least what format it is in?

---

### Post by CloudFX on 2008-10-20
Hi,

What application did you attempt this on?  It is possible that this application does not yet have a .desktop file, which is what makes it appear in your Main Menu.  You can also run the application by enter the it's name into a Terminal.

But for now, it's necessary for us to know the name of the application which you installed.

---

### Post by GrumpyGrenade on 2008-10-20
Oh, it is Wormux. I couldn't wait for the update so I downloaded the latest version off their site. :)

---

### Post by GrumpyGrenade on 2008-10-25
I have also recently downloaded Songbird. How would I go about putting Wormux and Songbird into the main menu? :confused:

---

### Post by geirha on 2008-10-25
Right click Applications on the top panel and select edit menus. Choose a suitable category, then click the New Item button. Click the browse button for the command field and select the executable file. Fill in the other fields as you wish.

---

### Post by GrumpyGrenade on 2008-10-26
I already tried that, it doesn't work because I also need all the other files in the folder. Is there a way I could upload the whole folder?

---

### Post by geirha on 2008-10-26
Oh, it must be run from the same directory as the executable is in? Then the easiest solution is to make a wrapper script that changes directory first, then executes.

```

#!/bin/sh
cd ~/Desktop/Songbird
exec ./songbird

```

Put the script wherever you like (~/bin perhaps), make it executable, and set the menu entry to launch that script instead.

---

### Post by GrumpyGrenade on 2008-10-27
Sorry if I'm just being ignorant but how exactly do I make it executable? And for Wormux could I just replace Songbird with Wormux?

---

### Post by geirha on 2008-10-27
> **GrumpyGrenade said:**
> Sorry if I'm just being ignorant but how exactly do I make it executable?  

Right click the file, select properties then select the permissions tab. In that tab you can select whether it should be executable or not. In a terminal you would do ```
chmod +x script-file.sh
``` to accomplish the same.

> **GrumpyGrenade said:**
> 
And for Wormux could I just replace Songbird with Wormux?

Yes replace ~/Desktop/Songbird with the path to Wormux (based on the screenshot it appears to be ~/Desktop/wormux-0.8.2-static-x86), and ./songbird to the executable file inside the Wormux folder (which appears to be ./wormux.sh).

---

### Post by GrumpyGrenade on 2008-10-28
Thank you so much. It has worked perfectly! :)

---

