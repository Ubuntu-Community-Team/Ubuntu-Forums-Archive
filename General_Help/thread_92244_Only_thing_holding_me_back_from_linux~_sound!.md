---
title: "Only thing holding me back from linux~ sound!"
date: 2005-11-19
forum: General Help
---

### Post by Sewage on 2005-11-19
Or lack there of. ):

I think it's because it doesn't detect my card~ I did the terminal comand to check my hardware and the sound card was not listed.

The card is verrry old~ The only things I know about it are what was written on the card:

Crystal
CX4235-XQ3
ZTAYKE9946
ALF119230

And that's all. ): 

I'm very new to linux and really have no idea what to do now, as far as I know I will never have sound. T_T

---

### Post by mykey on 2005-11-19
It sounds like an ISA card - which is really very old - plus configuration can be a real bitch - I advise you to go out and buy a simple cheap PCI card - it could save you lots of headaches .. 

good luck

---

### Post by Sewage on 2005-11-19
Also I am currently not in a postion to be buying new cards~ I don't see that as being helpful advice at all.

---

### Post by matthewv on 2005-11-19
add the following line to your /etc/modules
```
snd-cx4235
```
Post back here if it works (or doesn't)

---

### Post by Sewage on 2005-11-19
I logged on as root, went in to etc and edited the modules file by adding "snd-cx4235" to the end of it and saving~ Sadly it did not work. ):

Thank you for trying though.

---

### Post by jliedeka on 2005-11-19
You may want to search the LDP for isapnp stuff.  I remember struggling with an ISA Sound Blaster and ISA modem years ago with Red Hat 5.  I finally ended up jumpering the modem but the sound card had to be configured by ISAPNP.

Here's a link to the plug-n-play HOWTO: [http://www.linux.com/howtos/Plug-and-Play-HOWTO.shtml](http://www.linux.com/howtos/Plug-and-Play-HOWTO.shtml)

Since the card did not get recognized on install, I would also suggest checking your BIOS settings.  There used to a setting for whether or not you had a plug-n-play operating system.  You could try changing that setting.
     Jim

---

### Post by Sewage on 2005-11-19
I booted up the bios and saw an option for making it a "plug-n-play OS" so I enabled it~ No changes, no sound.

---

### Post by sylvester_0 on 2005-11-19
How old of a machine is this? If it does have PCI slots, that is the recommended action here. Someone will probably give you an old PCI card for free. If I didn't have to pay shipping, I'd send you one :).

---

### Post by Sewage on 2005-11-19
Yanno, I couldn't say how old it is~ 97'? hahaha~  I forget.

Anyway I was searching around and found another old card, an "aztech"? Is that more possible?

---

### Post by Efwis on 2005-11-19
[QUOTE=Sewage]Yanno, I couldn't say how old it is~ 97'? hahaha~  I forget.

Anyway I was searching around and found another old card, an "aztech"? Is that more possible?[/QUOTE]
lot better, but I would recommend checking this list to make sure it's supported. All the cards listed here are supported on OSS.

[http://www.opensound.com/osshw.html](http://www.opensound.com/osshw.html)

---

### Post by Sewage on 2005-11-20
I ended up just getting a new card~ everything works fine now.

Thanks those who tried to help. (:

---

### Post by mykey on 2005-12-06
:cool:

---

