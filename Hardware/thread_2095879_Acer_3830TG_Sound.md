---
title: "Acer 3830TG Sound"
date: 2012-12-18
forum: Hardware
---

### Post by Ventiti on 2012-12-18
Hello community.

As other users of the Acer 3830TG reported, there is a problem with the conexant cx20588 chip (sound) on Ubuntu 12.10. There is simply no sound. Some have already found some fixes and one of them is to enable the EAPD on the HDA Analyser. For that, I have to manage to run the HDA Analyser (like stated here: [http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)) which I, unfortunately, do not. I get this message in the terminal when prompting " python run.py" :

Using temporary directory: /dev/shm/hda-analyzer
You may remove this directory when finished or if you like to
download the most recent copy of hda-analyzer tool.
Downloading file hda_analyzer.py
Downloading file hda_guilib.py
Downloading file hda_codec.py
Downloading file hda_proc.py
Downloading file hda_graph.py
Downloading file hda_mixer.py
Downloaded all files, executing hda_analyzer.py
Codec 0/0 unavailable - permissions...
Codec 0/3 unavailable - permissions...
No HDA codecs were found or insufficient priviledges for 
/dev/snd/controlC* and /dev/snd/hwdepC*D* device files.

You may also check, if you compiled HDA driver with HWDEP
interface as well or close all application using HWDEP.

Try run this program as root user.



Can anyone help me since I am tired of windows 8 and want to completely move to Ubuntu?
[COLOR=DarkOrange]
Thank you very much.



EDIT: Solved !!!
[/COLOR]

---

