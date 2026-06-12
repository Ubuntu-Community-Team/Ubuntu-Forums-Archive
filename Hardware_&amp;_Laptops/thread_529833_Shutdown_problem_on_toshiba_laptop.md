---
title: "Shutdown problem on toshiba laptop"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by d11 on 2007-08-19
hello! i am new in linux, but i think that  is the best S.O that i've ever used.! i installed ubuntu feisty fawn on the toshiba laptop A130-135 dualcore 1.73.
all run very well, and the only problem is when i shutdown the system. all closed well but at the  end the process the  lcd monitor and the fan is still running and i have to turn off manually. y tried fixing it  modifying the grub whit: acpi=off, noapic, nolapic, apm=off, reboot -p and anything worked. maybe the problem is not in the grub. help me please.

---

### Post by ThrobbingBrain66 on 2007-08-19
Could you please paste the output of the following command here.
```
lsmod | grep intel
```

---

### Post by d11 on 2007-08-20
here is the output.

darvi@darvi-laptop:~$ lsmod | grep intel
snd_hda_intel          20504  2
snd_hda_codec         204160  1 snd_hda_intel
snd_pcm                76680  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    51716  14 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24348  1
agpgart                34096  3 drm,intel_agp
snd_page_alloc          9992  2 snd_hda_intel,snd_pcm
darvi@darvi-laptop:~$

---

### Post by d11 on 2007-08-20
i dont know why, but i think that my laptop doesnt finish the shutdown process only when i am using the  wired ethernet  card.THIS IS A  RTL8101E PCI EXPRESS FAST ETHERNET CARD. because when i am using the wireless card, the laptop complete the end process.

---

### Post by ThrobbingBrain66 on 2007-08-20
Give this command a shot while using both wireless and wired.  Before you shut down, issue this in a terminal
```
sudo rmmod esd snd_hda_intel
```

I have a toshiba as well with a shutdown problem.  But as soon as I unload the sound driver, it shuts down perfectly.

---

