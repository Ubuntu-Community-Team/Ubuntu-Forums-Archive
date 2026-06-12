---
title: "[Solved] Built in mic on DV4 HP laptops..."
date: 2009-03-09
forum: Hardware
---

### Post by warttack on 2009-03-09
I recently found out how to get internal mic working, it works for dv4 models but im sure it work for some other models too, and its easier than i though.

**First:**Open the terminal and do "**killall -9 pulseaudio**" then uninstall pulseaudio and install esound "**sudo apt-get remove pulseaudio**" and "**sudo apt-get install esound**", restart your pc. 

**Second:**Now go to the menubar click on system then preferences then sound. On the Sound Preferences window change every set to HDA Intel using (alsa) or the equivalent to your "card/sound driver". On "Default Mixer Tracks" choose the **Device:** "**HDA Intel**" or equivalent for ur "card/sound driver". 

**Third:** Right click on the sound icon in gnome-panel and click in "**Open volume control**" in volume control "**Device:**" should be "**HDA Intel(Alsa Mixer)**". Click on Preferences button unmark all recording devices there and mark the "**Digital Input Source - Options**". Now back to the "Volume Control" Window you should have a tab Options click on it and select "Digital mic 1" or equivalent dont use "Analog Inputs". From now on you should have your mic working, to set the volume you can use the alsamixer tru the terminal, for the ones who doesnt know how to do it, just type "alsamixer" on terminal window.

**Fourth:** Please leave a comment reporting if working or not for you... or vote on poll in the top of the page.

HAVE A GREAT TIME WITH YOUR WORKING BUILT IN MIC. ;)

---

### Post by rzsouza on 2009-03-30
Thanks mate, this worked perfectly.
I still have a small problem though, the sound quality is awful when I use skype, but it sounds perfect when I use sound recorder. Do you know what might be the problem?

Edit: After I changed the "sound in" in Skype from default to HDA Intel (hw:Intel,0) the quality is fine

---

### Post by rlj399 on 2009-05-29
I don't have the "digital input source- options"
My only options are "input source- options"
any suggestions?

---

### Post by macpattos on 2010-07-01
Hi, let me tell you that I follow your instructions on a HP DV4 1413la and the mic is still not working. Plus I lost my sound icon on the menu bar.

Any idea how to fix it?

Thanks

---

### Post by Charidan on 2011-09-14
I'm an a Sony VAIO VGN-AR150G. I uninstalled pulseaudio, installed esound, shut down, rebooted. Then when I tried to open the sound window it just said "Waiting for sound system to respond." Uhh, what's up with that? Did I manage to permanently break my sound?

---

