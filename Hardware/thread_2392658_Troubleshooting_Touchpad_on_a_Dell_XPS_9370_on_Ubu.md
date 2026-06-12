---
title: "Troubleshooting Touchpad on a Dell XPS 9370 on Ubuntu 18.04"
date: 2018-05-23
forum: Hardware
---

### Post by ryanchang on 2018-05-23
Hi all,

Up'd my Developer Edition (16.04) to 18.04--am not a developer, just a novice Ubuntu enthusiast. Upon upgrade, I didn't like how my mouse was scrolling, so I installed the synaptics driver, which changed my mouse settings to my pre-18.04 installation (more responsive, am able to scroll while also holding objects in the pointer, etc). However, now, if my palm even minutely swipes the trackpad, my cursor goes all over the place. 

After some initial troubleshooting, I discovered that **PalmDetect** is enabled, but doesn't seem to be doing anything. Many guides told me to configure the **synaptics.conf** file. However, I don't have one on my machine! Further, running **dmesg | grep -i touch** produces the following results:

```

[    1.821037] psmouse serio1: synaptics: Your touchpad (PNP: DLL07e6 PNP0f13) says it can support a different bus. If i2c-hid and hid-rmi are not used, you might want to try setting psmouse.synaptics_intertouch to 1 and report this to linux-input@vger.kernel.org.
[    1.876949] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.2, id: 0x1e2a1, caps: 0xf00323/0x840300/0x12e800/0x0, board id: 3038, fw id: 2375007
[    1.924397] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    2.540425] input: DELL07E6:00 06CB:76AF Touchpad as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-7/i2c-DELL07E6:00/0018:06CB:76AF.0001/input/input11
[    2.540500] hid-multitouch 0018:06CB:76AF.0001: input,hidraw0: I2C HID v1.00 Mouse [DELL07E6:00 06CB:76AF] on i2c-DELL07E6:00
[33867.630495] Modules linked in: thunderbolt ip6table_filter ip6_tables iptable_filter msr ccm rfcomm cmac bnep arc4 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 btusb videobuf2_core btrtl videodev btbcm media btintel bluetooth ecdh_generic snd_hda_codec_hdmi snd_soc_skl snd_soc_skl_ipc snd_hda_ext_core snd_soc_sst_dsp snd_soc_sst_ipc dell_smbios_smm dcdbas snd_soc_acpi hid_multitouch dell_laptop snd_hda_codec_realtek snd_hda_codec_generic snd_soc_core snd_compress ac97_bus nls_iso8859_1 snd_pcm_dmaengine intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc aesni_intel aes_x86_64 crypto_simd glue_helper cryptd intel_cstate intel_rapl_perf snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi
```

I see that two inputs are competing; the Synaptics TouchPad and my Dell. I'd read that this could cause problems -- could my palm swiping issue be due to the fact that there are competing touchpad drivers? Please advise.

Ryan

---

### Post by cruzer001 on 2018-05-23
Your XPS is set up different then my Dell Precision.   I do not get any output from "dmesg | grep -i touch" so I don't know about this interaction you mention and your method is different from the way I use to do it.  I now use libinput, but I have read where other Dell (xps) users have successfully replaced libinput with synaptics and claim it to be the better choice.

Does xinput list your touchpad?

```
xinput list
```

Make your changes using synclient.

[https://help.ubuntu.com/community/SynapticsTouchpad#Control_touchpad_features_using_synclient](https://help.ubuntu.com/community/SynapticsTouchpad#Control_touchpad_features_using_synclient)

[https://askubuntu.com/questions/290009/how-do-i-make-my-synclient-settings-stick](https://askubuntu.com/questions/290009/how-do-i-make-my-synclient-settings-stick)

[https://www.google.com/search?client=ubuntu&hs=ctK&channel=fs&ei=WfIFW6zhLbLq9AOtgbCICw&q=synclient+linux+ubuntu&oq=synclient+linux+ubuntu&gs_l=psy-ab.3...2183049.2195574.0.2196726.13.13.0.0.0.0.322.1645.6j6j0j1.13.0....0...1.1.64.psy-ab..0.12.1549...0j0i67k1j0i22i30k1j33i160k1j33i21k1.0.edItmDsyKwk](https://www.google.com/search?client=ubuntu&hs=ctK&channel=fs&ei=WfIFW6zhLbLq9AOtgbCICw&q=synclient+linux+ubuntu&oq=synclient+linux+ubuntu&gs_l=psy-ab.3...2183049.2195574.0.2196726.13.13.0.0.0.0.322.1645.6j6j0j1.13.0....0...1.1.64.psy-ab..0.12.1549...0j0i67k1j0i22i30k1j33i160k1j33i21k1.0.edItmDsyKwk)

---

### Post by vanadium on 2018-05-23
This may be of help to disable one of the two touchpad drivers: [http://ubuntuforums.org/showthread.php?t=2316240](http://ubuntuforums.org/showthread.php?t=2316240)

---

### Post by ryanchang on 2018-05-25
That command produces the following:

```
Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; DELL07E6:00 06CB:76AF Touchpad          	id=12	[slave  pointer  (2)] 
```

---

### Post by ryanchang on 2018-05-25
Thanks for this! I had come across this, lost it, then wasn't able to find it again.

Do you know if there are any adverse consequences if **libinput** is disabled?

---

### Post by cruzer001 on 2018-05-25
Synaptics once installed will override libinput.  Libinput is still installed in your system and can be enabled by removing synaptics.  Libinput is the newer gnome driver and synaptics will eventually be phased out, but at present they are both available and usable.

---

### Post by ryanchang on 2018-05-27
I uninstalled the synaptics driver, but now something strange has happened! Here's the output of **xinput list**

```
Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; DELL07E6:00 06CB:76AF Touchpad          	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=17	[slave  pointer  (2)]
```

Before, the Synaptics TouchPad was not showing up. 

I can confirm that libinput is being used, because previously, the issue I was experiencing with libinput was my mouse pointer jumping around.

---

### Post by cruzer001 on 2018-05-29
Sorry for the delay in response, been camping :)

For synaptics:
Check your current synaptics settings
Your code number from xinput is 17.
```
xinput list-props 17
```

An example of setting palm dimensions:
```
xinput set-prop 17 "Synaptics Palm Dimensions" 3, 3
```
Maybe 5, 5 or 3, 5 or ?  You will need to play with it.  First number is PalmMinWidth, second number is PalmMinZ.
All settings listed here
[ftp://www.x.org/pub/X11R7.5/doc/man/man4/synaptics.4.html](ftp://www.x.org/pub/X11R7.5/doc/man/man4/synaptics.4.html)

The above setting will work for one session and will not be saved.  One way to save custom settings is a startup file, plus any other changes can be added to it.
[https://askubuntu.com/questions/931761/how-to-fix-palm-rejection-on-ubuntu-16-04-lts](https://askubuntu.com/questions/931761/how-to-fix-palm-rejection-on-ubuntu-16-04-lts)

---

### Post by ryanchang on 2018-05-31
Thanks for the reply. Synaptics has disappeared, so I'm back on libinput.

However, I've noticed something strange that's been happening. After I use a hotkey combination (or a media key), or after a short length of inactivity, my touchpad will jump around on the screen upon touch. It's as if it speeds in the general direction of my desired movement (ie., if I want to move towards the upper left of the touchpad, the pointer will jump to the upper left corner, instead of only a short distance).

---

### Post by cruzer001 on 2018-05-31
Found something that's Ubuntu/libinput/XPS from Dell.

Check this out

[http://www.dell.com/support/article/us/en/04/sln308258/precision-xps-ubuntu-general-touchpad-mouse-issue-fix](http://www.dell.com/support/article/us/en/04/sln308258/precision-xps-ubuntu-general-touchpad-mouse-issue-fix)

---

### Post by jmfife on 2018-06-11
Exact same issue as @ryanchang here - Dell XPS-15, Ubuntu 18.04.  Using libinput with synaptics blacklisted.
When the touchpad is released for ~4 seconds or more, then swiped again, the cursor jumps dramatically.
Anyone have the same symptoms?
Anyone find a solution?

---

