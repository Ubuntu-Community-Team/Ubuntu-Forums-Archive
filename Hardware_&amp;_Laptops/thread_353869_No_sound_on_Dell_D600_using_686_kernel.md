---
title: "No sound on Dell D600 using 686 kernel"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by sventunus on 2007-02-05
Hi!

I'm running Edgy on my D600 and sound was working fine, untill I upgraded the kernel to 686 arch.
Now there is no sound at all and I can't seem to find a solution for it.
I allready tried adapting the menu.lst for GRUB like stated in other post, no success there.
Any wizards here who can help me out?

TIA!!

Sven

---

### Post by apjone on 2007-02-05
have you check the settings System > Preferance's > Sound? Also right click on the speaker and choose preferances. Check that your permisions aswell

---

### Post by sventunus on 2007-02-05
Hi, thanks for your reply!

Yes, I have tried that.
Have also tried everything that is said here: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Reinstalling ALSA didn't do the trick, and in trying to build the driver myself it failed.
Here is the failing output of the debugging logs.
Hope someone can help me, seems so strange that something that has worked is now causing so much trouble :( 

```

/usr/src/modules/alsa-driver/acore/sound.c:291: warning: passing           &#9618; 
 &#9474; argument 2 of ‘class_device_create’ makes pointer from integer without a   &#9618; 
 &#9474; cast                                                                       &#9618; 
 &#9474; /usr/src/modules/alsa-driver/acore/sound.c:291: warning: passing           &#9618; 
 &#9474; argument 3 of ‘class_device_create’ makes integer from pointer without a   &#9618; 
 &#9474; cast                                                                       &#9618; 
 &#9474; /usr/src/modules/alsa-driver/acore/sound.c:291: warning: passing           &#9646; 
 &#9474; argument 4 of ‘class_device_create’ from incompatible pointer type         &#9618; 
 &#9474; /usr/src/modules/alsa-driver/acore/sound.c:291: warning: passing           &#9618; 
 &#9474; argument 5 of ‘class_device_create’ discards qualifiers from pointer       &#9618; 
 &#9474; target type                                             
 CC [M]  /usr/src/modules/alsa-driver/acore/init.o                        &#8593; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/memory.o                      &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/info.o                        &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/control.o                     &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/misc.o                        &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/device.o                      &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/isadma.o                      &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/sound_oss.o                   &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/info_oss.o                    &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/wrappers.o                    &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/misc_driver.o                 &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/memory_debug.o                &#9646; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/snd.o                         &#9618; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/snd-hwdep.o                   &#9618; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/snd-timer.o      
 LD [M]  /usr/src/modules/alsa-driver/acore/snd-rtctimer.o                &#8593; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/snd-pcm.o                     &#9618; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/snd-page-alloc.o              &#9618; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/snd-rawmidi.o                 &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/oss/mixer_oss.o               &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/oss/pcm_oss.o                 &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/oss/pcm_plugin.o              &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/oss/io.o                      &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/oss/copy.o                    &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/oss/linear.o                  &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/oss/mulaw.o                   &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/oss/route.o                   &#9646; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/oss/rate.o                    &#9618; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/oss/snd-mixer-oss.o           &#9618; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/oss/snd-pcm-oss.o 
 CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_device.o              &#8593; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_dummy.o               &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_instr.o               &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_midi_emul.o           &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_midi_event.o          &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_midi.o                &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_virmidi.o             &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq.o                     &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_lock.o                &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_clientmgr.o           &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_memory.o              &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_queue.o               &#9646; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_fifo.o                &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_prioq.o               &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_timer.o 
 CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_system.o              &#8593; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_ports.o               &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/seq_info.o                &#9618; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/seq/snd-seq.o                 &#9618; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/seq/snd-seq-device.o          &#9618; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/seq/snd-seq-midi-event.o      &#9618; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/seq/snd-seq-dummy.o           &#9618; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/seq/snd-seq-virmidi.o         &#9618; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/seq/snd-seq-midi.o            &#9618; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/seq/snd-seq-midi-emul.o       &#9618; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/seq/snd-seq-instr.o           &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/instr/ainstr_fm.o         &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/instr/ainstr_gf1.o        &#9646; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/instr/ainstr_iw.o         &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/instr/ainstr_simple.o 
 LD [M]  /usr/src/modules/alsa-driver/acore/seq/instr/snd-ainstr-fm.o     &#8593; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/seq/instr/snd-ainstr-gf1.o    &#9618; 
 &#9474;   LD [M]                                                                   &#9618; 
 &#9474; /usr/src/modules/alsa-driver/acore/seq/instr/snd-ainstr-simple.o           &#9618; 
 &#9474;   LD [M]  /usr/src/modules/alsa-driver/acore/seq/instr/snd-ainstr-iw.o     &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss.o             &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_init.o        &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_timer.o       &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_ioctl.o       &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_event.o       &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_rw.o          &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_synth.o       &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_midi.o        &#9646; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_readq.o       &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/seq/oss/seq_oss_writeq.o 
 LD [M]  /usr/src/modules/alsa-driver/acore/seq/oss/snd-seq-oss.o         &#8593; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/drivers/aloop.o                     &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/drivers/dummy.o                     &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/drivers/mtpav.o                     &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/drivers/portman2x4.o                &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/drivers/serial-u16550.o             &#9618; 
 &#9474;   CC [M]  /usr/src/modules/alsa-driver/drivers/serialmidi.o                &#9618; 
 &#9474; /usr/src/modules/alsa-driver/drivers/serialmidi.c: In function ‘tx_loop’:  &#9618; 
 &#9474; /usr/src/modules/alsa-driver/drivers/serialmidi.c:317: error: ‘struct      &#9618; 
 &#9474; tty_struct’ has no member named ‘atomic_write’                             &#9618; 
 &#9474; /usr/src/modules/alsa-driver/drivers/serialmidi.c:322: error: ‘struct      &#9618; 
 &#9474; tty_struct’ has no member named ‘atomic_write’                             &#9618; 
 &#9474; /usr/src/modules/alsa-driver/drivers/serialmidi.c:339: error: ‘struct      &#9646; 
 &#9474; tty_struct’ has no member named ‘atomic_write’                             &#9618; 
 &#9474; make[6]: *** [/usr/src/modules/alsa-driver/drivers/serialmidi.o] Error 1
 make[5]: *** [/usr/src/modules/alsa-driver/drivers] Error 2                &#9618; 
 &#9474; make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2                &#9618; 
 &#9474; make[3]: *** [modules] Error 2                                             &#9618; 
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'      &#9618; 
 &#9474; make[2]: *** [compile] Error 2                                             &#9618; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618; 
 &#9474; make[1]: *** [build-stamp] Error 2                                         &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618; 
 &#9474; make: *** [kdist_image] Error 2           


```

---

