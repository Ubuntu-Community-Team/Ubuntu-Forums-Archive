---
title: "I can't patch the kernel"
date: 2010-11-21
forum: Hardware
---

### Post by ilcontegis on 2010-11-21
Hey guys I make one post more to give better visibility to this problem
I have a sony vaio TT and one of the main problems of this laptop is that the internal mic doesn't work.
[Here]("http://ubuntuforums.org/showthread.php?t=1111753") you can find all the info about the laptop.

Follows the guide I received to patch the kernel
> **konoko said:**
> ```
1. cd /usr/src/linux/sound/pci/hda
(go to the folder with the drivers)

2. wget -c http://launchpadlibrarian.net/48940908/vaiott.diff
(download patch from the above mentioned link)

3. patch -p0 --dry-run <vaiott.diff
(test patch with "--dry-run")

4. patch -p0 <vaiott.diff
(apply patch)
```now you have to recompile kernel modules. standard command to run is:
```
cd /usr/src/linux
make modules modules_install
```and reboot your machine.

I do not know whether debian/ubuntu has something special to rebuild kernel modules but I think that this should work anywhere.

You should probably read this Ubuntu howto and google little bit about compiling kernel on Debian/Ubuntu if you have never upgraded kernel manually:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Here is my error
```
teo@teo-vaio:/usr/src/linux/sound/pci/hda$ sudo patch -p0 --dry-run <vaiott.diffpatching file patch_realtek.c
Hunk #1 succeeded at 7087 (offset 150 lines).
Hunk #2 FAILED at 8862.
Hunk #3 FAILED at 10173.
2 out of 3 hunks FAILED -- saving rejects to file patch_realtek.c.rej
```

I installed everything that should be required, following [this guide]("https://help.ubuntu.com/community/Kernel/Compile") but I still get errors.  In installed more than 1 gb of things (actually I don't know if they were usefull.

Somebody could please explain me how can I apply this patch?

Thank you

---

### Post by Ayuthia on 2010-11-21
From the information that you provided, the patch was not successful.  It would be helpful if you can supply patch_realtek.c.rej (and the patch) and let us know which kernel version you are using (uname -a).  Most likely there have been changes to the kernel since that patch was created.

However, if this is an issue with the mic, have you tried installing the [alsa drivers]("http://www.alsa-project.org/main/index.php/Main_Page") so that you have the most recent drivers?  It might be easier than trying to patch the kernel and rebuild.

---

### Post by ilcontegis on 2010-11-21
> **Ayuthia said:**
> From the information that you provided, the patch was not successful.  It would be helpful if you can supply patch_realtek.c.rej (and the patch) and let us know which kernel version you are using (uname -a).  Most likely there have been changes to the kernel since that patch was created.

However, if this is an issue with the mic, have you tried installing the [alsa drivers]("http://www.alsa-project.org/main/index.php/Main_Page") so that you have the most recent drivers?  It might be easier than trying to patch the kernel and rebuild.

The Patch
```
--- patch_realtek.c.orig	2010-05-18 09:30:14.254249965 +0200
+++ patch_realtek.c	2010-05-22 17:43:36.581654312 +0200
@@ -6937,6 +6937,38 @@
 	},
 };
 
+static struct hda_input_mux alc883_vaiott_capture_sources[3] = {
+	/* Internal mic only available on one ADC */
+	{
+		.num_items = 5,
+		.items = {
+			{ "Ext Mic", 0x0 },
+			{ "Front Mic", 0x1 },
+			{ "Line In", 0x2 },
+			{ "CD", 0x4 },
+			{ "Int Mic", 0xb },
+		},
+	},
+	{
+		.num_items = 4,
+		.items = {
+			{ "Mic", 0x0 },
+			{ "Front Mic", 0x1 },
+			{ "Line In", 0x2 },
+			{ "CD", 0x4 },
+		},
+	},
+	{
+		.num_items = 4,
+		.items = {
+			{ "Mic", 0x0 },
+			{ "Front Mic", 0x1 },
+			{ "Line In", 0x2 },
+			{ "CD", 0x4 },
+		},
+	},
+};
+
 /*
  * 2ch mode
  */
@@ -8830,6 +8862,10 @@
 };
 
 static struct hda_verb alc883_vaiott_verbs[] = {
+	/* Internal Mic */
+	{0x12, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_VREF80},
+	{0x12, AC_VERB_SET_AMP_GAIN_MUTE, AMP_OUT_MUTE},
+	{0x24, AC_VERB_SET_CONNECT_SEL, 11},
 	/* HP */
 	{0x15, AC_VERB_SET_CONNECT_SEL, 0x00},
 	{0x15, AC_VERB_SET_PIN_WIDGET_CONTROL, PIN_HP},
@@ -10141,11 +10177,16 @@
 	[ALC883_SONY_VAIO_TT] = {
 		.mixers = { alc883_vaiott_mixer },
 		.init_verbs = { alc883_init_verbs, alc883_vaiott_verbs },
+		.adc_nids = alc882_adc_nids,
+		.num_adc_nids = ARRAY_SIZE(alc882_adc_nids),
+		.capsrc_nids = alc882_capsrc_nids,
 		.num_dacs = ARRAY_SIZE(alc883_dac_nids),
 		.dac_nids = alc883_dac_nids,
 		.num_channel_mode = ARRAY_SIZE(alc883_3ST_2ch_modes),
 		.channel_mode = alc883_3ST_2ch_modes,
-		.input_mux = &alc883_capture_source,
+		.num_mux_defs =
+			ARRAY_SIZE(alc883_vaiott_capture_sources),
+		.input_mux = alc883_vaiott_capture_sources,
 		.unsol_event = alc_automute_amp_unsol_event,
 		.setup = alc883_vaiott_setup,
 		.init_hook = alc_automute_amp,
```

patch_realtek.c.rej does not exist, i did a search of all the pc but i can't find it.


Kernel 2.6.35-23 (ubuntu 10.10 64bit), I think I have the most recent alsa driver. This problem is not new, since I bought the laptop I could not use the mic....
Thanks for your support

---

### Post by Decatf on 2010-11-21
Run **sudo updatedb** then do **locate patch_realtek.c.rej**

---

### Post by ilcontegis on 2010-11-21
> **Decatf said:**
> Run **sudo updatedb** then do **locate patch_realtek.c.rej**

something should happen?
```
teo@teo-vaio:~$ sudo updatedb
[sudo] password for teo: 
teo@teo-vaio:~$ locate patch_realtek.c.rej
teo@teo-vaio:~$ 

```

---

### Post by Decatf on 2010-11-21
That should list the file if it exists on the harddrive. The .rej file should be either in the same folder where you ran the patch command or the folder with the file that failed to patch... I can't remember which tbh.

---

### Post by ilcontegis on 2010-11-21
> **Decatf said:**
> That should list the file if it exists on the harddrive. The .rej file should be either in the same folder where you ran the patch command or the folder with the file that failed to patch... I can't remember which tbh.

So it means that I don't have this file in my pc? What else can I do?

Thank you for helping

---

### Post by Ayuthia on 2010-11-22
Please check /usr/src/linux/sound/pci/hda to see if it is there.

It will be helpful to see the .rej file if it is there, but it looks like the big portion of the patch was successful and the remaining parts are most likely are not lining up correctly.  It might be easier to go into patch_realtek.c and update it manually.  The first set of changes should be near line 8862 and the next set is close to 10173.  You just need to add the lines that contain the + and remove the lines that have -.

---

