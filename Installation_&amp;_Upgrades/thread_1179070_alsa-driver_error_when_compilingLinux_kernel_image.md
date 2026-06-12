---
title: "alsa-driver error when compilingLinux kernel image for version 2.6.28.11"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by ayman_sh on 2009-06-05
Hi,
I am getting alsa-driver error after upgrading my ubuntu server 8.10 t0 9.04,
I have Dell  xps m1210 laptop, the following error is appear with every restart for the system, It is attempts to compile the new kernel "image for version 2.6.28.11 server"

the log file is :

/var/run/alsa-driver.3010.log

rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/acore'
make -C ioctl32 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/ioctl32'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/ioctl32'
make -C oss mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp mixer_oss.c pcm_oss.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/oss'
make -C seq mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/seq'
make -C oss mrproper
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/seq/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp seq_oss.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/seq/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp seq.c seq_clientmgr.c seq_memory.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/seq'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp info.c pcm.c pcm_native.c control.c hwdep.c init.c rawmidi.c sound.c timer.c memalloc.c misc.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c'
make -C l3 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c/l3'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c/l3'
make -C other mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c/other'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c/other'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers'
make -C mpu401 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/mpu401'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp mpu401.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/mpu401'
make -C opl3 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/opl3'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp opl3_lib.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/opl3'
make -C opl4 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/opl4'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/opl4'
make -C pcsp mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/pcsp'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/pcsp'
make -C vx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp mts64.c portman2x4.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/isa'
make -C ad1816a mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/ad1816a'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/ad1816a'
make -C ad1848 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/ad1848'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/ad1848'
make -C cs423x mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/cs423x'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/cs423x'
make -C es1688 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/es1688'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/es1688'
make -C gus mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/gus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/gus'
make -C msnd mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/msnd'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/msnd'
make -C opti9xx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/opti9xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/opti9xx'
make -C sb mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/sb'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp sb16_csp.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/sb'
make -C wavefront mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/wavefront'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp wavefront_fx.c wavefront_synth.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/wavefront'
make -C wss mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/wss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/wss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/synth'
make -C emux mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/synth/emux'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/synth/emux'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/synth'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/pci'
make -C ac97 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ac97'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp ac97_codec.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ac97'
make -C ali5451 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ali5451'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp ali5451.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ali5451'
make -C asihpi mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/asihpi'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/asihpi'
make -C au88x0 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/au88x0'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp au88x0.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/au88x0'
make -C aw2 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/aw2'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/aw2'
make -C ca0106 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ca0106'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp ca0106_main.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ca0106'
make -C cs46xx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/cs46xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/cs46xx'
make -C cs5535audio mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/cs5535audio'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/cs5535audio'
make -C echoaudio mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/echoaudio'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp echoaudio.c darla20.c darla24.c echo3g.c gina20.c gina24.c indigo.c indigodj.c indigoio.c layla20.c layla24.c mia.c mona.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/echoaudio'
make -C emu10k1 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/emu10k1'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp emu10k1_main.c emu10k1x.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/emu10k1'
make -C hda mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/hda'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp hda_codec.c hda_beep.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/hda'
make -C ice1712 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ice1712'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ice1712'
make -C korg1212 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/korg1212'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp korg1212.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/korg1212'
make -C mixart mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/mixart'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/mixart'
make -C nm256 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/nm256'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/nm256'
make -C oxygen mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/oxygen'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/oxygen'
make -C pcxhr mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/pcxhr'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/pcxhr'
make -C pdplus mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/pdplus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/pdplus'
make -C riptide mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/riptide'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp riptide.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/riptide'
make -C rme9652 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/rme9652'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/rme9652'
make -C trident mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/trident'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/trident'
make -C vx222 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/vx222'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/vx222'
make -C ymfpci mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ymfpci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp ymfpci_main.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ymfpci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp ad1889.c atiixp.c atiixp_modem.c bt87x.c cmipci.c ens1370.c fm801.c intel8x0.c maestro3.c via82xx.c via82xx_modem.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa'
make -C codecs mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/codecs'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/codecs'
make -C core mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/core'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/core'
make -C fabrics mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/fabrics'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/fabrics'
make -C soundbus mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus'
make -C i2sbus mrproper
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus/i2sbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus/i2sbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/soc'
make -C at32 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/at32'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/at32'
make -C at91 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/at91'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/at91'
make -C au1x mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/au1x'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/au1x'
make -C blackfin mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/blackfin'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/blackfin'
make -C codecs mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/codecs'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/codecs'
make -C davinci mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/davinci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/davinci'
make -C fsl mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/fsl'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/fsl'
make -C omap mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/omap'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/omap'
make -C pxa mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/pxa'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/pxa'
make -C s3c24xx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/s3c24xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/s3c24xx'
make -C sh mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/sh'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/sh'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/usb'
make -C caiaq mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/usb/caiaq'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp caiaq-audio.c caiaq-device.c caiaq-input.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb/caiaq'
make -C usx2y mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/usb/usx2y'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp usX2Yhwdep.c usbusx2y.c usbusx2yaudio.c usx2yhwdeppcm.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb/usx2y'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp usbaudio.c usbmidi.c usbmixer.c
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia'
make -C pdaudiocf mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf'
make -C vx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/misc'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp 
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/misc'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/include'
rm -f .depend core *.o sndversions.h modules/*.ver modules/*.stamp
rm -f *.orig *.rej *~ .#*
rm -f linux/* asm/* media/*
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/include'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/test'
rm -f *.o mmap_test osspcm osspcm1 ossdelay
rm -f *~ *.orig *.rej .#*
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/test'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/utils'
rm -f *.orig *.rej *~ .#*
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/utils'
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
rm -f doc/*~
rm -f config.cache config.log config.status Makefile.conf
rm -f utils/alsa-driver.spec
rm -f `find alsa-kernel -name "*~"`
rm -f `find alsa-kernel -name "*.orig"`
rm -f `find alsa-kernel -name "*.rej"`
rm -f `find alsa-kernel -name ".#*"`
rm -f `find alsa-kernel -name "out.txt"`
rm -rf autom4te.cache
rm -f alsa-kernel/include/version.h
rm -f include/sound
rm -fr .tmp_versions
rm -f Module.symvers
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/lib/alsa-driver-linuxant
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.28-11-server/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.28-11-server
checking for GCC version... ./configure: eval: line 3967: syntax error near unexpected token `)'
./configure: eval: line 3967: `my_compiler_version=4.3.3-5ubuntu4)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for updating alsa-kernel version.h... yes
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking for deprecated linux/config.h... checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... no
Creating a dummy <asm/hw_irq.h>...
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/pm_qos_params.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... no
Creating a dummy <asm/irq_regs.h>...
checking for kernel linux/seq_file.h... yes
checking for kernel linux/debugfs.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... yes
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for pc-speaker input subsystem in kernel... module
checking for directory to store kernel modules... /lib/modules/2.6.28-11-server/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i686
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... no
checking for video_get_drvdata... yes
checking for V4L1 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver extra-version... 
checking for driver version... 1.0.18rc3
checking for dynamic minor numbers... no
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC support... no
checking for HPET support... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for GFP_DMA32... yes
checking for page_to_pfn... yes
checking for PnP suspend/resume... yes
checking for device_create_drvdata... no
checking for new unlocked/compat_ioctl... yes
checking for x86-compatible PC... yes
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for cards to compile driver for... all
checking for additonal options to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
if [ ! -d include/sound -a ! -L include/sound ]; then \
      ln -sf ../alsa-kernel/include include/sound ; \
    fi
cp -pvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make dep
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant'
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore'
copying file alsa-kernel/core/info.c
patching file info.c
copying file alsa-kernel/core/pcm.c
patching file pcm.c
Hunk #2 succeeded at 924 (offset 14 lines).
Hunk #3 succeeded at 940 (offset 14 lines).
Hunk #4 succeeded at 952 (offset 14 lines).
Hunk #5 succeeded at 1007 (offset 15 lines).
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
copying file alsa-kernel/core/control.c
patching file control.c
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
copying file alsa-kernel/core/init.c
patching file init.c
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #3 succeeded at 1293 (offset 4 lines).
Hunk #4 succeeded at 1377 (offset 4 lines).
copying file alsa-kernel/core/sound.c
patching file sound.c
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #3 succeeded at 997 (offset 5 lines).
Hunk #4 succeeded at 1919 (offset 5 lines).
Hunk #5 succeeded at 1964 (offset 5 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
Hunk #2 succeeded at 61 (offset -8 lines).
Hunk #3 succeeded at 210 (offset -8 lines).
Hunk #4 succeeded at 248 (offset -8 lines).
Hunk #5 succeeded at 270 (offset -8 lines).
Hunk #6 succeeded at 296 (offset -8 lines).
Hunk #7 succeeded at 314 (offset -8 lines).
Hunk #8 succeeded at 565 (offset -3 lines).
Hunk #9 succeeded at 704 (offset -3 lines).
Hunk #10 succeeded at 714 (offset -3 lines).
Hunk #11 succeeded at 753 (offset -3 lines).
copying file alsa-kernel/core/misc.c
patching file misc.c
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/ioctl32'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/ioctl32'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
Hunk #3 succeeded at 383 (offset 4 lines).
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
Hunk #3 succeeded at 2607 (offset 17 lines).
Hunk #4 succeeded at 2658 (offset 17 lines).
Hunk #5 succeeded at 2781 (offset 17 lines).
Hunk #6 succeeded at 2964 (offset 17 lines).
Hunk #7 succeeded at 3091 (offset 17 lines).
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/oss'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
Hunk #3 succeeded at 2209 (offset 6 lines).
Hunk #4 succeeded at 2561 (offset 10 lines).
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
Hunk #3 succeeded at 250 (offset 2 lines).
make[4]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
Hunk #3 succeeded at 192 (offset 3 lines).
Hunk #4 succeeded at 227 (offset 4 lines).
Hunk #5 succeeded at 330 (offset 4 lines).
make[4]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/seq/oss'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/seq'
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore'
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c/l3'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c/l3'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c/other'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c/other'
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c'
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers'
copying file alsa-kernel/drivers/mts64.c
patching file mts64.c
copying file alsa-kernel/drivers/portman2x4.c
patching file portman2x4.c
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/mpu401'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
Hunk #2 succeeded at 438 (offset 2 lines).
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/opl3'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/opl4'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/opl4'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/pcsp'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/pcsp'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/vx'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/vx'
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers'
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/ad1816a'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/ad1816a'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/ad1848'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/ad1848'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/cs423x'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/cs423x'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/es1688'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/es1688'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/gus'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/gus'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/msnd'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/msnd'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/opti9xx'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/opti9xx'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/sb'
copying file alsa-kernel/isa/sb/sb16_csp.c
patching file sb16_csp.c
Hunk #2 succeeded at 711 (offset 1 line).
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/sb'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/wavefront'
copying file alsa-kernel/isa/wavefront/wavefront_fx.c
patching file wavefront_fx.c
copying file alsa-kernel/isa/wavefront/wavefront_synth.c
patching file wavefront_synth.c
Hunk #2 succeeded at 1947 (offset 1 line).
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/wavefront'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/wss'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/wss'
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa'
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/synth'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/synth/emux'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/synth/emux'
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/synth'
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci'
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
copying file alsa-kernel/pci/atiixp.c
patching file atiixp.c
Hunk #2 succeeded at 1673 (offset 2 lines).
Hunk #3 succeeded at 1718 (offset 2 lines).
copying file alsa-kernel/pci/atiixp_modem.c
patching file atiixp_modem.c
Hunk #2 succeeded at 1313 (offset 6 lines).
Hunk #3 succeeded at 1356 (offset 6 lines).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #2 succeeded at 845 (offset -1 lines).
Hunk #3 succeeded at 999 (offset -1 lines).
copying file alsa-kernel/pci/cmipci.c
patching file cmipci.c
Hunk #2 succeeded at 3134 (offset -42 lines).
Hunk #3 succeeded at 3429 (offset -42 lines).
copying file alsa-kernel/pci/ens1370.c
patching file ens1370.c
Hunk #2 succeeded at 2120 (offset -11 lines).
Hunk #3 succeeded at 2496 (offset -11 lines).
copying file alsa-kernel/pci/fm801.c
patching file fm801.c
Hunk #2 succeeded at 1426 (offset 23 lines).
Hunk #3 succeeded at 1607 (offset 23 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #3 succeeded at 712 (offset 6 lines).
Hunk #4 succeeded at 722 (offset 6 lines).
Hunk #5 succeeded at 3167 (offset 39 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
Hunk #2 succeeded at 2596 (offset 4 lines).
Hunk #3 succeeded at 2777 (offset 4 lines).
copying file alsa-kernel/pci/via82xx.c
patching file via82xx.c
Hunk #2 succeeded at 2433 (offset -3 lines).
Hunk #3 succeeded at 2443 (offset -3 lines).
Hunk #4 succeeded at 2458 (offset -3 lines).
Hunk #5 succeeded at 2469 (offset -3 lines).
Hunk #6 succeeded at 2480 (offset -3 lines).
Hunk #7 succeeded at 2563 (offset -3 lines).
copying file alsa-kernel/pci/via82xx_modem.c
patching file via82xx_modem.c
Hunk #2 succeeded at 1184 (offset 4 lines).
Hunk #3 succeeded at 1244 (offset 4 lines).
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
Hunk #3 succeeded at 1914 (offset 3 lines).
Hunk #4 succeeded at 1926 (offset 3 lines).
Hunk #5 succeeded at 1950 (offset 3 lines).
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ac97'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ali5451'
copying file alsa-kernel/pci/ali5451/ali5451.c
patching file ali5451.c
Hunk #2 succeeded at 2207 (offset 2 lines).
Hunk #3 succeeded at 2377 (offset 2 lines).
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ali5451'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/asihpi'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/asihpi'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/au88x0'
copying file alsa-kernel/pci/au88x0/au88x0.c
patching file au88x0.c
Hunk #2 succeeded at 340 (offset -1 lines).
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/au88x0'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/aw2'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/aw2'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ca0106'
copying file alsa-kernel/pci/ca0106/ca0106_main.c
patching file ca0106_main.c
Hunk #3 succeeded at 1366 (offset 13 lines).
Hunk #4 succeeded at 1735 (offset 13 lines).
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ca0106'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/cs46xx'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/cs46xx'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/cs5535audio'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/cs5535audio'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/echoaudio'
copying file alsa-kernel/pci/echoaudio/echoaudio.c
patching file echoaudio.c
Hunk #1 succeeded at 1894 (offset -32 lines).
Hunk #2 succeeded at 1957 (offset -32 lines).
copying file alsa-kernel/pci/echoaudio/darla20.c
patching file darla20.c
copying file alsa-kernel/pci/echoaudio/darla24.c
patching file darla24.c
copying file alsa-kernel/pci/echoaudio/echo3g.c
patching file echo3g.c
copying file alsa-kernel/pci/echoaudio/gina20.c
patching file gina20.c
copying file alsa-kernel/pci/echoaudio/gina24.c
patching file gina24.c
copying file alsa-kernel/pci/echoaudio/indigo.c
patching file indigo.c
copying file alsa-kernel/pci/echoaudio/indigodj.c
patching file indigodj.c
copying file alsa-kernel/pci/echoaudio/indigoio.c
patching file indigoio.c
copying file alsa-kernel/pci/echoaudio/layla20.c
patching file layla20.c
copying file alsa-kernel/pci/echoaudio/layla24.c
patching file layla24.c
copying file alsa-kernel/pci/echoaudio/mia.c
patching file mia.c
copying file alsa-kernel/pci/echoaudio/mona.c
patching file mona.c
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/echoaudio'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/emu10k1'
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c
patching file emu10k1_main.c
Hunk #4 succeeded at 1406 (offset 1 line).
Hunk #5 succeeded at 1447 (offset 9 lines).
Hunk #6 succeeded at 1756 (offset 10 lines).
copying file alsa-kernel/pci/emu10k1/emu10k1x.c
patching file emu10k1x.c
Hunk #2 succeeded at 942 (offset 2 lines).
Hunk #3 succeeded at 1636 (offset 8 lines).
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/emu10k1'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/hda'
copying file alsa-kernel/pci/hda/hda_codec.c
patching file hda_codec.c
Hunk #2 succeeded at 328 (offset 49 lines).
Hunk #3 succeeded at 366 (offset 49 lines).
Hunk #4 succeeded at 381 (offset 49 lines).
Hunk #5 succeeded at 412 (offset 64 lines).
copying file alsa-kernel/pci/hda/hda_beep.c
patching file hda_beep.c
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/hda'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ice1712'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ice1712'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/korg1212'
copying file alsa-kernel/pci/korg1212/korg1212.c
patching file korg1212.c
Hunk #2 succeeded at 2342 (offset 3 lines).
Hunk #3 succeeded at 2498 (offset 3 lines).
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/korg1212'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/mixart'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/mixart'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/nm256'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/nm256'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/oxygen'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/oxygen'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/pcxhr'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/pcxhr'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/pdplus'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/pdplus'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #2 succeeded at 1280 (offset 1 line).
Hunk #3 succeeded at 2243 (offset 9 lines).
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/riptide'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/rme9652'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/rme9652'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/trident'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/trident'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/vx222'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/vx222'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ymfpci'
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c
patching file ymfpci_main.c
Hunk #2 succeeded at 2006 with fuzz 2 (offset -38 lines).
Hunk #3 succeeded at 2026 with fuzz 2 (offset -40 lines).
Hunk #4 succeeded at 2366 (offset -40 lines).
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ymfpci'
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci'
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/codecs'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/codecs'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/core'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/core'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/fabrics'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/fabrics'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus'
make[4]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus'
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa'
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/at32'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/at32'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/at91'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/at91'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/au1x'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/au1x'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/blackfin'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/blackfin'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/codecs'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/codecs'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/davinci'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/davinci'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/fsl'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/fsl'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/omap'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/omap'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/pxa'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/pxa'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/s3c24xx'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/s3c24xx'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/sh'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/sh'
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc'
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/usb'
copying file alsa-kernel/usb/usbaudio.c
patching file usbaudio.c
Hunk #2 succeeded at 70 with fuzz 2.
Hunk #3 succeeded at 689 (offset 30 lines).
Hunk #4 succeeded at 716 (offset 30 lines).
Hunk #5 succeeded at 797 with fuzz 2 (offset 30 lines).
Hunk #6 succeeded at 812 with fuzz 2 (offset 30 lines).
Hunk #7 succeeded at 1188 with fuzz 1 (offset 28 lines).
Hunk #8 succeeded at 2119 (offset 37 lines).
Hunk #9 succeeded at 2138 (offset 37 lines).
Hunk #10 succeeded at 2150 (offset 37 lines).
Hunk #11 succeeded at 2163 (offset 37 lines).
Hunk #12 succeeded at 2743 (offset 56 lines).
Hunk #13 succeeded at 2815 (offset 56 lines).
Hunk #14 succeeded at 3103 (offset 56 lines).
Hunk #15 succeeded at 3174 (offset 56 lines).
Hunk #16 succeeded at 3295 (offset 56 lines).
Hunk #17 succeeded at 3313 (offset 56 lines).
Hunk #18 succeeded at 3327 (offset 56 lines).
Hunk #19 succeeded at 3340 (offset 56 lines).
Hunk #20 succeeded at 3543 (offset 55 lines).
Hunk #21 succeeded at 3636 (offset 55 lines).
Hunk #22 succeeded at 3774 (offset 56 lines).
Hunk #23 succeeded at 3835 (offset 56 lines).
Hunk #24 succeeded at 3854 (offset 56 lines).
copying file alsa-kernel/usb/usbmidi.c
patching file usbmidi.c
Hunk #2 succeeded at 227 (offset 2 lines).
Hunk #3 succeeded at 251 (offset 2 lines).
Hunk #4 succeeded at 350 (offset 8 lines).
Hunk #5 succeeded at 1501 (offset 139 lines).
Hunk #6 succeeded at 1853 (offset 147 lines).
copying file alsa-kernel/usb/usbmixer.c
patching file usbmixer.c
Hunk #3 succeeded at 1737 (offset 2 lines).
Hunk #4 succeeded at 1786 (offset 2 lines).
Hunk #5 succeeded at 1807 (offset 2 lines).
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/usb/caiaq'
copying file alsa-kernel/usb/caiaq/caiaq-audio.c
patching file caiaq-audio.c
Hunk #1 succeeded at 1 with fuzz 2.
Hunk #2 succeeded at 448 with fuzz 1 (offset -13 lines).
Hunk #3 succeeded at 511 (offset -8 lines).
copying file alsa-kernel/usb/caiaq/caiaq-device.c
patching file caiaq-device.c
Hunk #2 succeeded at 120 (offset 6 lines).
Hunk #3 succeeded at 370 (offset 6 lines).
copying file alsa-kernel/usb/caiaq/caiaq-input.c
patching file caiaq-input.c
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb/caiaq'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
Hunk #11 succeeded at 1057 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb/usx2y'
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb'
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf'
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia/vx'
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia/vx'
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia'
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/misc'
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/misc'
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant'
make -C /lib/modules/2.6.28-11-server/build SUBDIRS=/usr/lib/alsa-driver-linuxant  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-server'
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/hwdep.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memory_wrapper.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memalloc.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/sgbuf.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_native.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_lib.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_timer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_misc.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_memory.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/rawmidi.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/timer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/wrappers.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/misc_driver.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/sound.o
/usr/lib/alsa-driver-linuxant/acore/sound.c: In function 'snd_request_other':
/usr/lib/alsa-driver-linuxant/acore/sound.c:99: warning: format not a string literal and no format arguments
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/init.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memory.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/info.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/control.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/misc.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/device.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/isadma.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/sound_oss.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/info_oss.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/vmaster.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/snd.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/snd-hwdep.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/snd-timer.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/snd-pcm.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/snd-page-alloc.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/snd-rawmidi.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/mixer_oss.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/pcm_oss.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/pcm_plugin.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/io.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/copy.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/linear.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/mulaw.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/route.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/oss/rate.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/oss/snd-mixer-oss.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/oss/snd-pcm-oss.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_device.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_dummy.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_midi_emul.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_midi_event.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_midi.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_virmidi.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_lock.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_clientmgr.o
/usr/lib/alsa-driver-linuxant/acore/seq/seq_clientmgr.c: In function 'snd_seq_info_dump_subscribers':
/usr/lib/alsa-driver-linuxant/acore/seq/seq_clientmgr.c:2465: warning: format not a string literal and no format arguments
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_memory.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_queue.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_fifo.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_prioq.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_timer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_system.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_ports.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/seq_info.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/snd-seq.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/snd-seq-device.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/snd-seq-midi-event.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/snd-seq-dummy.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/snd-seq-virmidi.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/snd-seq-midi.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/snd-seq-midi-emul.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_init.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_timer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_ioctl.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_event.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_rw.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_synth.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_midi.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_readq.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/seq_oss_writeq.o
  LD [M]  /usr/lib/alsa-driver-linuxant/acore/seq/oss/snd-seq-oss.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/aloop.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/dummy.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/mtpav.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/mts64.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/portman2x4.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/serial-u16550.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/virmidi.o
  LD [M]  /usr/lib/alsa-driver-linuxant/drivers/snd-aloop.o
  LD [M]  /usr/lib/alsa-driver-linuxant/drivers/snd-dummy.o
  LD [M]  /usr/lib/alsa-driver-linuxant/drivers/snd-virmidi.o
  LD [M]  /usr/lib/alsa-driver-linuxant/drivers/snd-serial-u16550.o
  LD [M]  /usr/lib/alsa-driver-linuxant/drivers/snd-mtpav.o
  LD [M]  /usr/lib/alsa-driver-linuxant/drivers/snd-mts64.o
  LD [M]  /usr/lib/alsa-driver-linuxant/drivers/snd-portman2x4.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/mpu401/mpu401_uart.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/mpu401/mpu401.o
  LD [M]  /usr/lib/alsa-driver-linuxant/drivers/mpu401/snd-mpu401-uart.o
  LD [M]  /usr/lib/alsa-driver-linuxant/drivers/mpu401/snd-mpu401.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/opl3_lib.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/opl3_synth.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/opl3_seq.o
In file included from /usr/lib/alsa-driver-linuxant/drivers/opl3/opl3_seq.c:2:
/usr/lib/alsa-driver-linuxant/drivers/opl3/../../alsa-kernel/drivers/opl3/opl3_seq.c: In function 'snd_opl3_seq_new_device':
/usr/lib/alsa-driver-linuxant/drivers/opl3/../../alsa-kernel/drivers/opl3/opl3_seq.c:238: warning: format not a string literal and no format arguments
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/opl3_midi.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/opl3_drums.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/opl3_oss.o
  LD [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/snd-opl3-lib.o
  LD [M]  /usr/lib/alsa-driver-linuxant/drivers/opl3/snd-opl3-synth.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/opl4_lib.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/opl4_mixer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/opl4_proc.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/opl4_seq.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/opl4_synth.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/yrw801.o
  LD [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/snd-opl4-lib.o
  LD [M]  /usr/lib/alsa-driver-linuxant/drivers/opl4/snd-opl4-synth.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/vx/vx_core.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/vx/vx_hwdep.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/vx/vx_pcm.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/vx/vx_mixer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/vx/vx_cmd.o
  CC [M]  /usr/lib/alsa-driver-linuxant/drivers/vx/vx_uer.o
  LD [M]  /usr/lib/alsa-driver-linuxant/drivers/vx/snd-vx-lib.o
  CC [M]  /usr/lib/alsa-driver-linuxant/i2c/cs8427.o
  CC [M]  /usr/lib/alsa-driver-linuxant/i2c/i2c.o
  CC [M]  /usr/lib/alsa-driver-linuxant/i2c/tea6330t.o
  LD [M]  /usr/lib/alsa-driver-linuxant/i2c/snd-tea6330t.o
  LD [M]  /usr/lib/alsa-driver-linuxant/i2c/snd-i2c.o
  LD [M]  /usr/lib/alsa-driver-linuxant/i2c/snd-cs8427.o
  CC [M]  /usr/lib/alsa-driver-linuxant/i2c/other/ak4114.o
  CC [M]  /usr/lib/alsa-driver-linuxant/i2c/other/ak4117.o
  CC [M]  /usr/lib/alsa-driver-linuxant/i2c/other/ak4xxx-adda.o
  CC [M]  /usr/lib/alsa-driver-linuxant/i2c/other/pt2258.o
  LD [M]  /usr/lib/alsa-driver-linuxant/i2c/other/snd-ak4117.o
  LD [M]  /usr/lib/alsa-driver-linuxant/i2c/other/snd-ak4xxx-adda.o
  LD [M]  /usr/lib/alsa-driver-linuxant/i2c/other/snd-ak4114.o
  LD [M]  /usr/lib/alsa-driver-linuxant/i2c/other/snd-pt2258.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/adlib.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/als100.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/azt2320.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/cmi8330.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/dt019x.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/es18xx.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/opl3sa2.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sc6000.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sgalaxy.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sscape.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-adlib.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-als100.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-azt2320.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-cmi8330.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-dt019x.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-es18xx.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-opl3sa2.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-sc6000.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-sgalaxy.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/snd-sscape.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/ad1816a/ad1816a.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/ad1816a/ad1816a_lib.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/ad1816a/snd-ad1816a.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/ad1848/ad1848.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/ad1848/snd-ad1848.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/cs423x/cs4231.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/cs423x/cs4232.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/cs423x/cs4236_lib.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/cs423x/cs4236.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/cs423x/snd-cs4231.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/cs423x/snd-cs4232.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/cs423x/snd-cs4236.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/cs423x/snd-cs4236-lib.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/es1688/es1688_lib.o
In file included from /usr/lib/alsa-driver-linuxant/isa/es1688/es1688_lib.c:2:
/usr/lib/alsa-driver-linuxant/isa/es1688/../../alsa-kernel/isa/es1688/es1688_lib.c: In function 'snd_es1688_pcm':
/usr/lib/alsa-driver-linuxant/isa/es1688/../../alsa-kernel/isa/es1688/es1688_lib.c:739: warning: format not a string literal and no format arguments
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/es1688/es1688.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/es1688/snd-es1688.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/es1688/snd-es1688-lib.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_main.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_io.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_irq.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_timer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_mem.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_mem_proc.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_dram.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_dma.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_volume.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_pcm.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_mixer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_uart.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gus_reset.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gusclassic.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gusextreme.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/gusmax.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/interwave-stb.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/gus/interwave.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/gus/snd-gusclassic.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/gus/snd-gus-lib.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/gus/snd-gusmax.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/gus/snd-gusextreme.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/gus/snd-interwave.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/gus/snd-interwave-stb.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/msnd/msnd.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/msnd/msnd_pinnacle.o
/usr/lib/alsa-driver-linuxant/isa/msnd/msnd_pinnacle.c: In function 'upload_dsp_code':
/usr/lib/alsa-driver-linuxant/isa/msnd/msnd_pinnacle.c:726: warning: assignment discards qualifiers from pointer target type
/usr/lib/alsa-driver-linuxant/isa/msnd/msnd_pinnacle.c:728: warning: assignment discards qualifiers from pointer target type
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/msnd/msnd_pinnacle_mixer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/msnd/msnd_midi.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/msnd/snd-msnd-pinnacle.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/miro.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/opti92x-ad1848.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/opti92x-cs4231.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/opti93x.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/snd-opti92x-ad1848.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/snd-opti92x-cs4231.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/snd-opti93x.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/opti9xx/snd-miro.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/emu8000_synth.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/emu8000_callback.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/emu8000_patch.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/emu8000_pcm.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/es968.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb_common.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb_mixer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb16_csp.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb16_main.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb16.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb8_main.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb8_midi.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sb8.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/sbawe.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/sb/emu8000.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-sb-common.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-sb16-dsp.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-sb8-dsp.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-sb8.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-sb16.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-sbawe.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-es968.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-sb16-csp.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/sb/snd-emu8000-synth.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/wavefront/wavefront.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/wavefront/wavefront_fx.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/wavefront/wavefront_synth.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/wavefront/wavefront_midi.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/wavefront/snd-wavefront.o
  CC [M]  /usr/lib/alsa-driver-linuxant/isa/wss/wss_lib.o
  LD [M]  /usr/lib/alsa-driver-linuxant/isa/wss/snd-wss-lib.o
  CC [M]  /usr/lib/alsa-driver-linuxant/misc/ac97_bus.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ad1889.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/als300.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/als4000.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/atiixp_modem.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/atiixp.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/azt3328.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/bt87x.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/cmipci.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/cs4281.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/cs5530.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ens1370.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ak4531_codec.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ens1371.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/es1938.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/es1968.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/fm801.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/intel8x0.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/intel8x0m.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/maestro3.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/rme32.o
In file included from /usr/lib/alsa-driver-linuxant/pci/rme32.c:2:
/usr/lib/alsa-driver-linuxant/pci/../alsa-kernel/pci/rme32.c: In function 'snd_rme32_proc_read':
/usr/lib/alsa-driver-linuxant/pci/../alsa-kernel/pci/rme32.c:1473: warning: format not a string literal and no format arguments
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/rme96.o
In file included from /usr/lib/alsa-driver-linuxant/pci/rme96.c:2:
/usr/lib/alsa-driver-linuxant/pci/../alsa-kernel/pci/rme96.c: In function 'snd_rme96_proc_read':
/usr/lib/alsa-driver-linuxant/pci/../alsa-kernel/pci/rme96.c:1673: warning: format not a string literal and no format arguments
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/sis7019.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/sonicvibes.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/via82xx_modem.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/via82xx.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-ad1889.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-als300.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-als4000.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-atiixp.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-atiixp-modem.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-azt3328.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-bt87x.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-cmipci.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-cs4281.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-cs5530.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-ens1370.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-ens1371.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-es1938.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-es1968.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-fm801.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-intel8x0.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-intel8x0m.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-maestro3.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-rme32.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-rme96.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-sis7019.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-sonicvibes.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-via82xx.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/snd-via82xx-modem.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ac97/ac97_codec.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ac97/ac97_pcm.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ac97/ac97_proc.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/ac97/snd-ac97-codec.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ali5451/ali5451.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/ali5451/snd-ali5451.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/asihpi.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpioctl.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpimsginit.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpicmn.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpifunc.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpidebug.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpidspcd.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpios_linux_kernel.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpi6000.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpi6205.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/hpimsgx.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/asihpi/snd-asihpi.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/au88x0/au8810.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/au88x0/au8820.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/au88x0/au8830.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/au88x0/snd-au8810.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/au88x0/snd-au8820.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/au88x0/snd-au8830.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/aw2/aw2-alsa.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/aw2/aw2-saa7146.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/aw2/snd-aw2.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ca0106/ca0106_main.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ca0106/ca0106_proc.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ca0106/ca0106_mixer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ca0106/ca_midi.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/ca0106/snd-ca0106.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/cs46xx/cs46xx.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/cs46xx/cs46xx_lib.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/cs46xx/dsp_spos.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/cs46xx/dsp_spos_scb_lib.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/cs46xx/snd-cs46xx.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/cs5535audio/cs5535audio.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/cs5535audio/cs5535audio_pcm.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/cs5535audio/cs5535audio_pm.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/cs5535audio/snd-cs5535audio.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/darla20.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/darla24.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/echo3g.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/gina20.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/gina24.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/indigo.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/indigodj.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/indigoio.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/layla20.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/layla24.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/mia.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/mona.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/snd-darla20.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/snd-gina20.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/snd-layla20.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/snd-darla24.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/snd-gina24.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/snd-layla24.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/snd-mona.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/snd-mia.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/snd-echo3g.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/snd-indigo.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/snd-indigoio.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/echoaudio/snd-indigodj.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/emu10k1_synth.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/emu10k1_callback.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/emu10k1_patch.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/emu10k1.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/emu10k1_main.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/irq.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/memory.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/voice.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/emumpu401.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/emupcm.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/io.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/emuproc.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/emumixer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/emufx.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/timer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/p16v.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/emu10k1x.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/snd-emu10k1.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/snd-emu10k1-synth.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/emu10k1/snd-emu10k1x.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/hda/hda_intel.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/hda/hda_codec.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/hda/hda_proc.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/hda/hda_hwdep.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/hda/hda_beep.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/hda/hda_generic.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/hda/patch_realtek.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/hda/patch_cmedia.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/hda/patch_analog.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/hda/patch_sigmatel.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/hda/patch_si3054.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/hda/patch_atihdmi.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/hda/patch_conexant.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/hda/patch_via.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/hda/snd-hda-intel.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/ice1712.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/delta.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/hoontech.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/ews.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/ice1724.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/amp.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/revo.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/aureon.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/vt1720_mobo.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/pontis.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/prodigy192.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/prodigy_hifi.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/juli.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/phase.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/wtm.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/se.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/ak4xxx.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/snd-ice1712.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/snd-ice17xx-ak4xxx.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/ice1712/snd-ice1724.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/korg1212/korg1212.o
/usr/lib/alsa-driver-linuxant/pci/korg1212/korg1212.c: In function 'snd_korg1212_proc_read':
/usr/lib/alsa-driver-linuxant/pci/korg1212/korg1212.c:2063: warning: format not a string literal and no format arguments
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/korg1212/snd-korg1212.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/mixart/mixart.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/mixart/mixart_core.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/mixart/mixart_hwdep.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/mixart/mixart_mixer.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/mixart/snd-mixart.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/nm256/nm256.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/nm256/snd-nm256.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/oxygen/hifier.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/oxygen/oxygen_io.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/oxygen/oxygen_lib.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/oxygen/oxygen_mixer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/oxygen/oxygen_pcm.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/oxygen/oxygen.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/oxygen/virtuoso.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/oxygen/snd-oxygen-lib.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/oxygen/snd-hifier.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/oxygen/snd-oxygen.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/oxygen/snd-virtuoso.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/pcxhr/pcxhr.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/pcxhr/pcxhr_hwdep.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/pcxhr/pcxhr_mixer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/pcxhr/pcxhr_core.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/pcxhr/snd-pcxhr.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/pdplus/pdplus.o
/usr/lib/alsa-driver-linuxant/pci/pdplus/pdplus.c: In function 'pdplus_proc_read':
/usr/lib/alsa-driver-linuxant/pci/pdplus/pdplus.c:5528: warning: format not a string literal and no format arguments
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/pdplus/snd-pdplus.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/riptide/riptide.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/riptide/snd-riptide.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/rme9652/hdsp.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/rme9652/hdspm.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/rme9652/rme9652.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/rme9652/snd-rme9652.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/rme9652/snd-hdsp.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/rme9652/snd-hdspm.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/trident/trident.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/trident/trident_main.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/trident/trident_memory.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/trident/snd-trident.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/vx222/vx222.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/vx222/vx222_ops.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/vx222/snd-vx222.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ymfpci/ymfpci.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pci/ymfpci/ymfpci_main.o
  LD [M]  /usr/lib/alsa-driver-linuxant/pci/ymfpci/snd-ymfpci.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf/pdaudiocf.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf/pdaudiocf_core.o
  CC [M]  /usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf/pdaudiocf_irq.o
In file included from /usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf/pdaudiocf_irq.c:3:
/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf/../../alsa-kernel/pcmcia/pdaudiocf/pdaudiocf_irq.c: In function 'pdacf_interrupt':
/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf/../../alsa-kernel/pcmcia/pdaudiocf/pdaudiocf_irq.c:48: error: implicit declaration of function 'get_irq_regs'
/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf/../../alsa-kernel/pcmcia/pdaudiocf/pdaudiocf_irq.c:48: warning: comparison between pointer and integer
make[4]: *** [/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf/pdaudiocf_irq.o]** Error 1**
make[3]: *** [/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf] Error 2
make[2]: *** [/usr/lib/alsa-driver-linuxant/pcmcia]** Error 2**
make[1]: *** [_module_/usr/lib/alsa-driver-linuxant]** Error 2**
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-server'
make: *** [compile] Error 2
     
**Please any help?**
[B]
Thanks.
 [/B]

---

### Post by ayman_sh on 2009-06-13
Any replies please help.

Thanks

---

