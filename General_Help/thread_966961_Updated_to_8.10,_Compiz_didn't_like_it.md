---
title: "Updated to 8.10, Compiz didn't like it"
date: 2008-11-01
forum: General Help
---

### Post by jaymz on 2008-11-01
Ok, so I upgraded today and everything seemed fine.

And everything IS fine as long as I use metacity.

But I happen to be a very fond user of compiz and Avant Window Navigator, so I really hope I don't have to go back to Metacity.

Right here, in metacity, if I type 

```
soulfly@Primitive:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: ATI Mobility Radeon X1400

```

But in Compiz

```
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
```

I've tried installing the graphics card driver both using Envy and using the official method, none have given me any better results.

Everything SEEMS to be working, I have effects, Avant works... But everything's very glitchy and the video playback works VERY poorly...

Please help?

PS: My graphics card is ATI Mobility Radeon X1400

---

### Post by thewolffman on 2008-11-01
same problem here. Did a fresh install of 8.10 and same
bad compiz / video.

glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: ATI Mobility Radeon HD 2600


when i disable compiz than everything is ok...

---

### Post by loomsen on 2008-11-02
Yet again the protobuf extensions could do miracles...

[I point at it here](http://ubuntuforums.org/showpost.php?p=6073711&postcount=2)

[HowTo get rid of your actual compiz](http://ubuntuforums.org/showpost.php?p=6085477&postcount=20)

If you want...

---

### Post by jaymz on 2008-11-08
EDIT: Ok, so that was just me being stupid.

Still, I can't seem to be able to get the key.

Are you sure everything is spelt correctly?

You did forget the "install" in the last line.

---

### Post by m_cubed on 2008-11-09
Ok so I upgraded as well, and after the upgrade compiz no longer works.

When I try compiz --replace the computer spits out something about XGL not being present and falls back to metacity.  I tried glxinfo | grep render with this effect

```
triplem@Serenity:/etc/X11$ glxinfo | grep render
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

I also tried the command without the parameters:

```
triplem@Serenity:/etc/X11$ glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

I miss my eye candy :cry:

---

### Post by thomascj on 2008-11-12
i'm experiencing the same problem -- lack (functioning) of fglrx driver.  no option to install it via the jockey-gtk "hardware drivers" as there was before.  did I miss something?

---

