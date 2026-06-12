---
title: "nVidia Realtek ALC1200 sound card no longer detected"
date: 2009-03-04
forum: Hardware
---

### Post by Jerrac on 2009-03-04
For some reason Ubuntu 8.10 64bit has stopped detecting my sound card. At least I think that is the problem.

After I installed it a few days ago, I had to install the nVidia 177 drivers to get sound working. But today, I boot up and there is suddenly no sound. Clicking on the volume control applet gives me this error:
> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

System->Preferences->Sound gives me this error when I test.
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

I read through a bunch of topics and tried a bunch of stuff. Nothing has worked so far. Though after I reinstalled a bunch of gstreamer stuff in Synaptic, I can use my volume control again.

I went through these topics:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)
[http://ubuntuforums.org/showthread.php?t=1047005](http://ubuntuforums.org/showthread.php?t=1047005)
And a few others....

I also tried turning off the nvidia drivers, restarting, turning on the 173 drivers, and restarting, didn't work. So I went back to the 177 drivers.

lspci:
> sudo lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation Device 0ad0 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:14.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200 (rev a2)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)


>  aplay -l
aplay: device_list:215: no soundcards found...


Anything else I can try?

---

### Post by Chemical Imbalance on 2009-03-12
Same exact thing here:
 nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)

except aplay -l here does print out my soundcard correctly

---

### Post by Jerrac on 2009-03-12
> **Chemical Imbalance said:**
> Same exact thing here:
 nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)

except aplay -l here does print out my soundcard correctly

I ended up upgrading to Jaunty... It works fine now. I think you could try upgrading to the latest driver from NVIDIA. I started to do that under Intrepid, but never finished... It's number is 180.something.

---

### Post by Chemical Imbalance on 2009-03-12
> **Jerrac said:**
> I ended up upgrading to Jaunty... It works fine now. I think you could try upgrading to the latest driver from NVIDIA. I started to do that under Intrepid, but never finished... It's number is 180.something.

Glad to hear it works in Jaunty!  I'll try upgrading the driver
thanks

---

