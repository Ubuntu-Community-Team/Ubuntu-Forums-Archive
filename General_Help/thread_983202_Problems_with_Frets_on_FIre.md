---
title: "Problems with Frets on FIre"
date: 2008-11-15
forum: General Help
---

### Post by Sinani201 on 2008-11-15
Well, the Windows version for this game was giving me weird problems, so I'm using Linux version this time.

For those of you who don't know what Frets on Fire is, it's a game similar to Guitar Hero where you "rock out with your keyboard." It's very fun.

Anyways, the game used to work fine, but then I realized that the screen resolution (in the game) was messed up. When I changed it, the game closed, and now whenever I open it, the screen goes black for about a split-second, then I go back to the desktop. I've tried running the game in every resolution, but I keep getting the same problem. I have re-installed it a billion times, I've deleted the configuration file and re-installed it again, and a bunch of other stuff.

One of the problems may be that it's running in the "Wine Programs Loader," when it's not supposed to be running with Wine. It's also a shell script, while all of the other game files are "normal" files. Also, when I ran "Hardware Testing," I didn't pass the video test. In addition, if I type fretsonfire in the terminal, I get this:

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x87
  Serial number of failed request:  123
  Current serial number in output stream:  125

Does anyone know why this is happening? Someone please help.

---

### Post by Sinani201 on 2008-11-15
Sorry for the double-post, but I really need help. Can someone please reply?

---

### Post by Strog on 2008-11-24
I have exactly the same problem... When I try to start the game I get this error:

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x8b
  Serial number of failed request:  155
  Current serial number in output stream:  157

And just like the Sinani201 the problem poped up when I tried to change the resolution of the game...

[edit]

LOL... I solved the problem :D.

Go to the ~/.fretsonfire/
and edit fretsonfire.ini and set the resolution manually.

That fixed the problem for me!

---

