---
title: "Z3735F stick - No Sound, No Media Playback"
date: 2016-02-22
forum: Hardware
---

### Post by Pratham on 2016-02-22
I have a Intel Z3735 based mini stick PC which is almost same as Meegopad T02. I have installed Ubuntu 14.04 on it by following instructions at 
[https://plus.google.com/+IanMORRISON/posts/UNWdwRMqy3j](https://plus.google.com/+IanMORRISON/posts/UNWdwRMqy3j)

So basically, I have installed a 32bit boot loader, installed z3735f drivers and a dsdt patch for sound to work. And everything boots fine. But I still don't get any sound. 

This is basically what the dsdt patch does:

```
Device (HAD)
        {
            Name (_ADR, Zero)  
            Name (_HID, "HAD0F28")  
            Name (_CID, "HAD0F28") 
            Name (_DDN, "Intel(R) HDMI Audio Driver - HAD")  
            Name (_UID, One)  
            Method (_STA, 0, NotSerialized)  
            {
                If (And (OSSL, 0x80))
                {
                    Return (0x0F)
                }

                Return (0x0F) // Before patching this was "Return (Zero)"
            }
```

Some of the things I have noticed:
1) Before installing the dsdt patch, sound settings says dummy output. However, media files at least play in Rhythmbox, Videos app and Firefox (just without sound). On clicking the Left and Right Speaker "Test" buttons in sound settings, they turn to "Stop" and after few seconds back to "Test" which is the expected behavior. However,

2) After installing the dsdt patch, I do get Analog output INTELHDMI in sound settings. But what happens is none of the media files play in Rhythmbox, Videos app, Firefox, Smplayer. Playback just remain at 0:00 and does not move forward. Even in sound tests, Left and Right Speaker "Test" buttons, on click, just remain at "Stop" and not turn back to "Test". So even the test sounds are not playing.

a```
play -l:

card 0: IntelHDMI [IntelHDMI], device 0: IntelHDMI [IntelHDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0
```

dmesg:
[http://pastebin.com/0mm3Tb03](http://pastebin.com/0mm3Tb03)

I am not expert in this. But this are the things that seem suspicious to me in dmesg:

1)```
[6.953118] WARNING: CPU: 0 PID: 196 at  /var/lib/dkms/oem-audio-i915-baytrail/0.20150605/build/i915/intel_sideband.c:200  vlv_dpio_read+0x71/0x80 [i915]()
```

2) ```
[6.953671] [drm:intel_pipe_config_compare] *ERROR*  mismatch in adjusted_mode.flags(DRM_MODE_FLAG_NHSYNC) (expected 2, found  0)
[6.953675] ------------[ cut here ]------------

 [6.953709] WARNING: CPU: 0 PID: 196 at  /var/lib/dkms/oem-audio-i915-baytrail/0.20150605/build/i915/intel_display.c:10202  check_crtc_state+0x703/0xd70 [i915]()

 [6.953712] pipe state doesn't match!

```
3)```
[5.779201] had: ******** HAD DRIVER loading.. Ver: 0.01.003
[5.780167] [drm] mid_hdmi_audio_register: Scheduling HDMI audio work queue

 [5.780190] [drm:i915_had_wq] *ERROR* Checking for HDMI connection at boot

```
Any help to get the sound working with Ubuntu 14.04 / Linux 3.16 will be much appreciated. Since, the WiFi drivers for RTL8723BS are based on Linux 3.16, I don't think I can upgrade to a later version as of now. 

Thank You

---

### Post by gordintoronto on 2016-02-22
I have never had a good experience with a Linux version which is older than the hardware. Could you try 15.10?

Also, it's a low-performance computer, so Xubuntu or Lubuntu might be a better choice than Ubuntu.

---

### Post by Bluppie on 2016-02-25
On my Medion Akoya i3 laptop 3 years old after update kernel no sound. Ubuntu 15.10

---

