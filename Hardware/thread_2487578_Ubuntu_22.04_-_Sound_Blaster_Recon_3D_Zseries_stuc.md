---
title: "Ubuntu 22.04 - Sound Blaster Recon 3D Zseries stuck on S/Pdif"
date: 2023-06-08
forum: Hardware
---

### Post by BrassCat on 2023-06-08
Hello the forum. New build for me. 2 months running.
Older Win 7 Opteron 6128 machine. 22.04 now.

trying to get audio out from sound card. Have gone into
Settings / Sound. Try to select audio out drop box,
only choice is digital audio out S/Pdif. ???? (? because of no other choice)

What should I be doing to get analog audio out selected ?

Thanks, BrassCat

---

### Post by dE_logics on 2023-06-08
There must be something in the audio settings by which you select the 'profile'. Here you can select 'Analog stereo duplex'.

If you cannot get this, there must be some command starting with name pavucontrol* -- this commonly named pavucontrol-gtk or pavucontrol-qt.

Run this command, you'll be greeted with a GPU application, where you can select 'Analog stereo duplex'.

---

### Post by BrassCat on 2023-06-12
Thanks for the reply. Unfortunetly it did not help.

I installed and ran pavucontrol. As before, the drop box only
has the digital audio out S/Pdif. no other option.

---

