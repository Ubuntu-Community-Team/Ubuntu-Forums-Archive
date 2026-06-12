---
title: "Digital Video/sound export problems using KINO"
date: 2005-12-06
forum: General Help
---

### Post by GMachine_24 on 2005-12-06
Hi:

I have Breezy installed and Kino 0.7.5. I can import a .dv file from my JVC camera but have no luck exporting the file to MPEG - or any other format. Here are the error messages I get:


>>> ExportMJPEG::startExport
>>> Generated video pipe ' mpeg2enc -v 0 -f 3 -I 1 -n n -a 2 -b 4000 -o '/home/e rikm/hdb2/eriks/eriks'.mpv'
>>> Generated audio pipe '|mp2enc -v 0  -o '/home/erikm/hdb2/eriks/eriks'.mp2'
sh: mp2enc: command not found
sh: mpeg2enc: command not found

(kino:8844): Gtk-WARNING **: Ignoring the separator setting
>>> Executing 'mplex -v 0 -f 3 -o '/home/erikm/hdb2/eriks/eriks'.mpeg '/home/eri km/hdb2/eriks/eriks'.mpv '/home/erikm/hdb2/eriks/eriks'.mp2'
sh: mplex: command not found

<end>

It seems neither the mp2enc no mpeg2enc commands can be found. I have installed all related mpg packages that I could find - does anyone have any ideas? Thanks.

GMachine

---

