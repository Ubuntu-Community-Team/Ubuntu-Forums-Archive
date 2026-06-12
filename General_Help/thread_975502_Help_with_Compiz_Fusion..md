---
title: "Help with Compiz Fusion."
date: 2008-11-08
forum: General Help
---

### Post by Starecase on 2008-11-08
I need to enable custom desktop effects but I keep getting this error.

"Desktop effects could not be enabled."

Any clue what's going on and how I can fix it?

---

### Post by Starecase on 2008-11-08
I need help, please guys.

---

### Post by hictio on 2008-11-08
What video card do you have?
Are you running Intrepid?

Get the model of your video card like this, open a Terminal (Applications -> Accesories -> Terminal), and type:
```

lshw -c display

```

You'll see something like this:
```

esteban@tango:~$ lshw -c display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: GeForce 7000M (rev a2)
       vendor: nVidia Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia
esteban@tango:~$ 

```

I have an NVIDIA GeForce 7000M on my laptop, which can deliver Desktop Effects.

Another thing, try this script: [compiz-check](http://forlong.blogage.de/entries/pages/Compiz-Check).

---

### Post by Starecase on 2008-11-08
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-display UNCLAIMED
       description: VGA compatible controller
       product: NV44A [GeForce 6200]
       vendor: nVidia Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=248 maxlatency=1 mingnt=5



Uhh.. not sure what Intrepid is. Care to exlpain?


Also, what is Super-User?

---

### Post by hictio on 2008-11-08
Intrepid is the version of Ubuntu you are running.
Is it 8.04 (Hardy) or 8.10 (Intrepid Ibex) that you are running?

Super User is the administrator user of your box, when you execute a command on the Terminal with the command, 'sudo' you are executing that program as the administrator.

---

### Post by Starecase on 2008-11-08
I'm running 8.10. Can I still use Compiz?

And why does it say my display is UNCLAIMED?

---

### Post by hictio on 2008-11-08
> **Starecase said:**
> I'm running 8.10. Can I still use Compiz?

And why does it say my display is UNCLAIMED?


Well, the ability to use it is related not only to the Ubuntu version you are running, but also to the video card that you have.
What is your Ubuntu box? A laptop or a desktop? If a desktop, what monitor do you have?

---

