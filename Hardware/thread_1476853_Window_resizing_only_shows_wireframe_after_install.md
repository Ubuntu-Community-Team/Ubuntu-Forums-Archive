---
title: "Window resizing only shows wireframe after installing NVidia drivers"
date: 2010-05-08
forum: Hardware
---

### Post by kellywashere on 2010-05-08
Hey guys,

With my fresh install of Ubuntu 10.04, while resizing windows their contents are shown (which is what I like). However, after installing the newest NVidia drivers for my GeForce 8400M GS, this feature seems to have disappeared, showing only a lame wireframe when resizing. The Metacity settings have not changed (reduced_resources is still unchecked).
This problem also occurs for the slightly older 173 version of the NVidia drivers.

Anybody's got a clue as to how to fix this?

Thanks,
Kelly

---

### Post by dino99 on 2010-05-08
look at hardware driver (system admin) if nvidia-current is activated.

nvidia-current, nvidia-current-modaliases, nvidia-common and nvidia-settings need to be installed (system admin synaptic)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by kellywashere on 2010-05-08
Yes, the driver is activated, and the packages are all installed. Also, updating as suggested does not change anything.
I noticed that the switch reduced_resources (gconf-editor apps->metacity->general) does not have the same effect as before installing the NVidia drivers: before, checking the switch would give a wireframe that looks like an empty tic-tac-toe board; after installation, the wireframe is only a rectangle and the state of the reduced_resources switch has no influence on it. To make sure Metacity was still managing the windows, I altered some other things, which had te expected effect...

---

### Post by kellywashere on 2010-05-08
Solved!
I gave myself a good hint in my reply before... Apparently, installing the drivers did change the window manger to Compiz.

Actually, from [https://help.ubuntu.com/community/Metacity](https://help.ubuntu.com/community/Metacity) I read


[LIST]
[*]   Once the *Appearance* tab is open by  either method, select the *Visual Effects* tab and click on *None*.   
[*]Note: Selecting a choice other than *None*  will  exit *Metacity* and start *Compiz* if hardware permits.
[/LIST]
Anyway, I still don't fully understand why making changes in apps->Metacity has effects when I'm not even running it, but that's just cause I'm a total newb I guess... Maybe somebody is kind enough to answer me that last piece of the "puzzle".

Regards,
Kelly

---

### Post by dino99 on 2010-05-08
a theme issue ?

metacity --replace

---

