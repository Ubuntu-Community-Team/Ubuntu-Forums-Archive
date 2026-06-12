---
title: "Problem with SCSI modules"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by tontonrico on 2005-12-22
Hello,

First, sorry for my bad english (my native language is french).

I experienced problems on my Breezy (there were not problems with Hoary and Warty) with the scsi modules on the 2.6.12-10 kernel.

This is the second time the problem occurs. I noticed errors messages about some scsi modules during the boot. Hereafter what I see when I list the directory :

##################################
[B][COLOR="Red"]ls /lib/modules/2.6.12-10-386/kernel/drivers/scsi/
ls: /lib/modules/2.6.12-10-386/kernel/drivers/scsi/ppa.ko: Erreur d'entrée/sortie
ls: /lib/modules/2.6.12-10-386/kernel/drivers/scsi/sata_qstor.ko: Erreur d'entrée/sortie
ls: /lib/modules/2.6.12-10-386/kernel/drivers/scsi/sata_sis.ko: Erreur d'entrée/sortie
ls: /lib/modules/2.6.12-10-386/kernel/drivers/scsi/sata_sx4.ko: Erreur d'entrée/sortie
ls: /lib/modules/2.6.12-10-386/kernel/drivers/scsi/sata_via.ko: Erreur d'entrée/sortie
ls: /lib/modules/2.6.12-10-386/kernel/drivers/scsi/sata_vsc.ko: Erreur d'entrée/sortie
ls: /lib/modules/2.6.12-10-386/kernel/drivers/scsi/scsi_debug.ko: Erreur d'entrée/sortie
ls: /lib/modules/2.6.12-10-386/kernel/drivers/scsi/scsi_transport_iscsi.ko: Erreur d'entrée/sortie[/COLOR][/B]
3w-9xxx.ko      BusLogic.ko        ibmmca.ko      NCR53C9x.ko      qlogicisp.ko           st.ko
3w-xxxx.ko      ch.ko              ide-scsi.ko    NCR_D700.ko      sata_nv.ko             sym53c416.ko
53c700.ko       dc395x.ko          imm.ko         NCR_Q720_mod.ko  sata_promise.ko        sym53c8xx_2
aacraid         dmx3191d.ko        in2000.ko      nsp32.ko         sata_sil.ko            t128.ko
advansys.ko     dpt_i2o.ko         initio.ko      osst.ko          sata_svw.ko            tmscsim.ko
aha152x.ko      dtc.ko             ipr.ko         pas16.ko         sata_uli.ko            u14-34f.ko
aha1542.ko      eata.ko            ips.ko         pcmcia           scsi_mod.ko            ultrastor.ko
aha1740.ko      eata_pio.ko        libata.ko      psi240i.ko       scsi_transport_fc.ko   wd7000.ko
ahci.ko         fd_mcs.ko          lpfc           qla1280.ko       scsi_transport_spi.ko
aic7xxx         fdomain.ko         mca_53c9x.ko   qla2xxx          sd_mod.ko
aic7xxx_old.ko  gdth.ko            megaraid       qlogicfas408.ko  sg.ko
ata_piix.ko     g_NCR5380.ko       megaraid.ko    qlogicfas.ko     sim710.ko
atp870u.ko      g_NCR5380_mmio.ko  NCR53c406a.ko  qlogicfc.ko      sr_mod.ko
####################################

The message "**Erreur d'entrée/sortie**" in english is "[COLOR="Red"]I/O error [/COLOR]".

This is the second time it occurs, the first time I solved the problem with a "fsck /dev/hda" and a re-installation of the kernel. During 2 weeks, it worked correctly and now the problem is re-appeared.

I did not "play" with my config. I can not understand where comes from this problem (except maybe a hardware incompatibility).

If you want, you can check my posts in the french site ([http://forum.ubuntu-fr.org/viewtopic.php?id=20708](http://forum.ubuntu-fr.org/viewtopic.php?id=20708) and [http://forum.ubuntu-fr.org/viewtopic.php?id=21811)](http://forum.ubuntu-fr.org/viewtopic.php?id=21811)).

My hardware is an Asus A7V8xx MB with an Athlon 1800XP. I have also a card reader from HAMA (maybe the problem ?).

So, could you help me to understand and if possible to avoid this problem ?

See you.

---

### Post by tontonrico on 2005-12-30
Hello,

Since a kernel upgrade to 2.6.10-24, it works corectly.


Bye

---

