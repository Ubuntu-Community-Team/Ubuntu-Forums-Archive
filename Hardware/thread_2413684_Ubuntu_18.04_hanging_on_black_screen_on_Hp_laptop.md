---
title: "Ubuntu 18.04 hanging on black screen on Hp laptop"
date: 2019-02-28
forum: Hardware
---

### Post by 21weberer on 2019-02-28
Hi, so I have a HP Pavilion 15-cx0056wm gaming laptop that I am doing a dual-boot setup with Windows 10 and Ubuntu 18.04, in UEFI mode for both. when I attempt to run Ubuntu, it hangs at the booting screen. When looking at the loading text (I'm not sure how else to describe it) it hangs at the disk [FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]journaling phase (from when I had to force shutdown). Does anyone know what I need to do? Legacy support is enabled, it still runs UEFI, TPM is enabled, [FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]virtualization,[/FONT] is disabled, not sure what else to post. Thanks![/FONT]

---

### Post by mastablasta on 2019-03-01
run fsck for starters: [https://askubuntu.com/questions/885062/root-file-system-requires-manual-fsck/885085](https://askubuntu.com/questions/885062/root-file-system-requires-manual-fsck/885085)

---

### Post by 21weberer on 2019-03-01
Ok, I will do that. I will run some of the other utilities in the recovery mode as well. Any other tips for when I start the process?
UPDATE: i have found a workaround. I can get into the operating system by loading recovery mode, then resuming normal boot. I still cannot boot normally, but i can access the OS now. the utilities have not seemed to help though. Is there something wrong to cause me to only have to use the recovery mode? thanks.

---

