---
title: "Alsa snd_pcm_open segmentation fault"
date: 2016-10-21
forum: Hardware
---

### Post by carcox on 2016-10-21
I am trying to open an audio interface on my desktop device, by calling the ALSA Api function:.


```
    int err;
    short buf[128];
    snd_pcm_t *playback_handle;
    snd_pcm_hw_params_t *hw_params;
    
    if ((err = snd_pcm_open (&playback_handle, "hw:0,0", SND_PCM_STREAM_PLAYBACK, 0)) < 0) {
        fprintf (stderr, "cannot open audio device %s (%s)\n", 
             argv[1],
             snd_strerror (err));
        exit (1);
    }
```


I compile the code (alsa_test.c) by giving the command:
```
`gcc -o alsa_test alsa_test.c -L/usr/libx86_64-linux-gnu -lasound`
```


And everything compiles fine (I get some warnings but they do not regard the snd_pcm_open function)


But when I run the application I get a segmentation fault (core dumped) at the invocation of snd_pcm_open(...).
I checked my audio devices by calling aplay -l and the output is:


```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC270 Analog [ALC270 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


It appears that I have the audio drivers correctly installed, so I really do not know what could be the problem.


I have Ubuntu 16.04 64 bit installed on an Intel x86_64 architecture.


Thanks in advance

---

