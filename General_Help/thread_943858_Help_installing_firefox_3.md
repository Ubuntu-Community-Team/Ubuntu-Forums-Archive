---
title: "Help installing firefox 3"
date: 2008-10-10
forum: General Help
---

### Post by stepbystep on 2008-10-10
:lolflag:Can someone give me a stepbystep guide as to how to download the latest version of firefox.

:guitar:I know how to download it.

:confused:I am just clueless as to what to do from there.
          I know another window comes up and you have to extract or open.
          It is from there that I don't get. Do I extract or can I just open?

:KSAny help appreciated. I am using firefox 2. But it does not have the option for me to enlarge screen. Only font size.

\\:D/I need firefox 3 as it has this option

---

### Post by Pumalite on 2008-10-10
Save file to Desktop. Then in Terminal:

cd ~/Desktop
tar xvzf firefox-3.0.3.tar.gz
cd firefox
./firefox

Make sure Firefox is closed when you do this.

---

### Post by aysiu on 2008-10-10
> **Pumalite said:**
> Save file to Desktop. Then in Terminal:

cd ~/Desktop
tar xvzf firefox-3.0.3.tar.gz
cd firefox
./firefox

Make sure Firefox is closed when you do this.
But that won't link it to plugins or the launcher for Firefox.

These instructions should help you:
[http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal)

---

### Post by Pumalite on 2008-10-10
Thanks. I learned something new.

---

### Post by stepbystep on 2008-10-10
> **aysiu said:**
> But that won't link it to plugins or the launcher for Firefox.

These instructions should help you:
[http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal)

Great. Used the link, but I cannot find and or locate firefox3.
I went to synaptic manager and downloaded anything that said firefox 3, but can't find the shortcut.

Downloading from ubuntu is quite hard.

Never know how to extract.

Did the terminal command. After that I couldn't even locate firefox 3.

I might be better off going back to windows.

---

### Post by aysiu on 2008-10-10
So you have Firefox 3 in Synaptic? What did you download the .tar.bz2 for, then?

I'm not sure what you mean about not being able to "locate" Firefox 3. What happens when you paste this command into the terminal? ```
firefox &
``` Does Firefox launch or not?

---

