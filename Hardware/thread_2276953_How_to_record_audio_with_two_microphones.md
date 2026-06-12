---
title: "How to record audio with two microphones?"
date: 2015-05-05
forum: Hardware
---

### Post by Fryser on 2015-05-05
I already have "Jack" installed in my computer. I looked all over the net but I can't find a satisfying answer to something I thing should be pretty straight forward.

[COLOR=#0000ff][SIZE=4]What I want:[/SIZE][/COLOR]
I want to plug two microphones on my (Microphone + Line-In) ports and have "Jack" manage the "Capture_1" + "Capture_2" + "Capture_3" + "Capture_4" to send it to "Ardour" and record the two microphone simultaneously on two different channel. 

[COLOR=#0000ff]What I get:[/COLOR]
I get the normal "Capture_1" + "Capture_2" that is selected on the "Ubuntu Sound panel">"input". If I have "line-in" selected, well Line-In work but not the microphone. The same goes when I select the microphone", Line-In won't work.

[COLOR=#0000FF]Question:
[/COLOR]How do I setup my system to add other capture port on the my jack server?

------------------------------------------------------------------------------------
I have a  [Intel® Desktop Board DX48BT2]("http://www.intel.com/support/motherboards/desktop/dx48bt2/sb/CS-029390.htm") | (Ubuntu 14.01)
[IMG]http://techgage.com/reviews/ecs/x48t-a/intel_x48bt2_08_thumb.jpg[/IMG]
[COLOR=#0000cd]~$ cat /proc/asound/cards[/COLOR]
[COLOR=#006400] 0 [Intel          ]: HDA-Intel - HDA Intel[/COLOR]
[COLOR=#006400]                      HDA Intel at 0xe3220000 irq 20[/COLOR]
[COLOR=#006400] 1 [U0x46d0x825    ]: USB-Audio - USB Device 0x46d:0x825[/COLOR]
[COLOR=#006400]                      USB Device 0x46d:0x825 at usb-0000:00:1a.7-6, high speed[/COLOR]
[COLOR=#0000cd]~$ aplay -l[/COLOR]
[COLOR=#006400]**** List of PLAYBACK Hardware Devices ****[/COLOR]
[COLOR=#006400]card 0: Intel [HDA Intel], device 0: STAC9274D Analog [STAC9274D Analog][/COLOR]
[COLOR=#006400]  Subdevices: 1/1[/COLOR]
[COLOR=#006400]  Subdevice #0: subdevice #0[/COLOR]
[COLOR=#006400]card 0: Intel [HDA Intel], device 1: STAC9274D Digital [STAC9274D Digital][/COLOR]
[COLOR=#006400]  Subdevices: 1/1[/COLOR]
[COLOR=#006400]  Subdevice #0: subdevice #0[/COLOR]

---

### Post by tgalati4 on 2015-05-06
Most on-board sound chips have an audio router that allows you to select either or (line or mic, but not both).  If you have a stereo microphone input, then you could separate the two channels and record them separately.  If you study the chip architecture for your specific Intel sound chip, it becomes clear that audio is just one of several functions performed by the chip and multichannel flexibility is not one of those functions.

You would need an M-Audio or similar sound card that has a multichannel audio router.  All of the channels will be displayed and you can create a [patch bay]("https://code.google.com/p/mudita24/wiki/Mudita24UbuntuStudio1010BetaTheme") that mixes and matches inputs and outputs for your recording session.

---

### Post by Fryser on 2015-05-06
That make sense. Thx brah :guitar:

---

### Post by osmoma on 2015-05-07
(i hope this is not irrelevant to your question)
1) Audio-recorder can record from many devices, but the recorded result is a mixed audio file.
Ref: [https://launchpad.net/~audio-recorder](https://launchpad.net/~audio-recorder)

In the main GUI, select `User defined audio source`.
And in the settings choose the devices (webcams, mics, sound cards, etc) that you want to record from.
[[IMG]http://bildr.no/thumb/VG51N3d3.jpeg[/IMG]]("http://bildr.no/view/VG51N3d3")

2) You can see the actual Gstreamer command used for recording in  
Additional Settings --> Recording Commands -> "Show Cmd" dialog.
[[IMG]http://bildr.no/thumb/bVVDRFJa.jpeg[/IMG]]("http://bildr.no/view/bVVDRFJa")
It may help you to compose your own recording pipeline (assuming you are running Ubuntu 15.04 vivid).

---

