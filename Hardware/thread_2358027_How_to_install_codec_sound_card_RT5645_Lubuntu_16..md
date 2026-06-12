---
title: "How to install codec sound card RT5645 Lubuntu 16.04"
date: 2017-04-08
forum: Hardware
---

### Post by nagato-02 on 2017-04-08
[FONT=-moz-fixed]Hi, 
My name is Esteban. 
I have a problem with my sound card. 
My sound card is a Realtek 5645 running on Asus x205ta. 
I using ubuntu 16.04.2 LTS of 64 bits. 
This is that i received when i type in the console:  pulseaudio -v 

ozzz@ozzz-pc:~$ pulseaudio -v 
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed:  Operación no permitida 
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed:  Operación no permitida 
I: [pulseaudio] core-util.c: Successfully gained nice level -11. 
I: [pulseaudio] main.c: This is PulseAudio 8.0 
I: [pulseaudio] main.c: Page size is 4096 bytes 
I: [pulseaudio] main.c: Machine ID is 3f31ce2cf2964000b4f65a8aec055d57. 
I: [pulseaudio] main.c: Session ID is c2. 
I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse. 
I: [pulseaudio] main.c: Using state directory [I]/home/ozzz/.config/pulse. 
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-8.0/modules. 
I: [pulseaudio] main.c: Running in system mode: no 
W: [pulseaudio] pid.c: Stale PID file, overwriting. 
I: [pulseaudio] main.c: System supports high resolution timers 
I: [pulseaudio] cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3  SSE4_1 SSE4_2 
I: [pulseaudio] svolume_mmx.c: Initialising MMX optimized volume functions. 
I: [pulseaudio] remap_mmx.c: Initialising MMX optimized remappers. 
I: [pulseaudio] svolume_sse.c: Initialising SSE2 optimized volume functions. 
I: [pulseaudio] remap_sse.c: Initialising SSE2 optimized remappers. 
I: [pulseaudio] sconv_sse.c: Initialising SSE2 optimized conversions. 
I: [pulseaudio] svolume_orc.c: Initialising ORC optimized volume functions. 
I: [pulseaudio] module-device-restore.c: Successfully opened database  file  '[I]/home/ozzz/.config/pulse/3f31ce2cf2964000b4f65a8aec055d57-device-volumes'. 
I: [pulseaudio] module.c: Loaded "module-device-restore" (index: #0;  argument: ""). 
I: [pulseaudio] module-stream-restore.c: Successfully opened database  file  '[I]/home/ozzz/.config/pulse/3f31ce2cf2964000b4f65a8aec055d57-stream-volumes'. 
I: [pulseaudio] module.c: Loaded "module-stream-restore" (index: #1;  argument: ""). 
I: [pulseaudio] module-card-restore.c: Successfully opened database file  '[I]/home/ozzz/.config/pulse/3f31ce2cf2964000b4f65a8aec055d57-card-database'. 
I: [pulseaudio] module.c: Loaded "module-card-restore" (index: #2;  argument: ""). 
I: [pulseaudio] module.c: Loaded "module-augment-properties" (index: #3;  argument: ""). 
I: [pulseaudio] module.c: Loaded "module-switch-on-port-available"  (index: #4; argument: ""). 
I: [pulseaudio] (alsa-lib)utils.c: could not open configuration file  /usr/share/alsa/ucm/Intel HDMI/DP LPE Audio/Intel HDMI/DP LPE Audio.conf 
I: [pulseaudio] (alsa-lib)parser.c: error: could not parse configuration  for card Intel HDMI/DP LPE Audio 
I: [pulseaudio] (alsa-lib)main.c: error: failed to import Intel HDMI/DP  LPE Audio use case configuration -2 
I: [pulseaudio] alsa-ucm.c: UCM not available for card Intel HDMI/DP LPE  Audio 
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2) 
I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No existe el  archivo o el directorio 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM front:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device front:0: Argumento  inválido 
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2) 
I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No existe el  archivo o el directorio 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM iec958:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0:  Argumento inválido 
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on  plug:hw:0: Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM front:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device front:0: Argumento  inválido 
I: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_buffer_size_near()  failed: Argumento inválido 
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0' 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM surround21:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device surround21:0:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM surround40:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device surround40:0:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM surround41:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device surround41:0:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM surround50:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device surround50:0:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM surround51:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device surround51:0:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM surround71:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device surround71:0:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM iec958:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0:  Argumento inválido 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No existe  el archivo o el directorio 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No existe  el archivo o el directorio 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dca:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device dca:0: No existe  el archivo o el directorio 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: Argumento  inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: Argumento  inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: Argumento  inválido 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dcahdmi:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device dcahdmi:0: No  existe el archivo o el directorio 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,1 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,1 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,1 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,1 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,1 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,1 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1:  Argumento inválido 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dcahdmi:0,1 
I: [pulseaudio] alsa-util.c: Error opening PCM device dcahdmi:0,1: No  existe el archivo o el directorio 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,2 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,2 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,2 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,2 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,2 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,2 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2:  Argumento inválido 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dcahdmi:0,2 
I: [pulseaudio] alsa-util.c: Error opening PCM device dcahdmi:0,2: No  existe el archivo o el directorio 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,3 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,3 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,3 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,3 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,3 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,3 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3:  Argumento inválido 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dcahdmi:0,3 
I: [pulseaudio] alsa-util.c: Error opening PCM device dcahdmi:0,3: No  existe el archivo o el directorio 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,4 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,4 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,4:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,4 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,4 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,4:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,4 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,4 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,4:  Argumento inválido 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dcahdmi:0,4 
I: [pulseaudio] alsa-util.c: Error opening PCM device dcahdmi:0,4: No  existe el archivo o el directorio 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,5 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,5 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,5:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,5 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,5 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,5:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,5 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,5 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,5:  Argumento inválido 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dcahdmi:0,5 
I: [pulseaudio] alsa-util.c: Error opening PCM device dcahdmi:0,5: No  existe el archivo o el directorio 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,6 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,6 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,6:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,6 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,6 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,6:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,6 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,6 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,6:  Argumento inválido 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dcahdmi:0,6 
I: [pulseaudio] alsa-util.c: Error opening PCM device dcahdmi:0,6: No  existe el archivo o el directorio 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,7 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,7 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,7:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,7 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,7 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,7:  Argumento inválido 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0,7 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,7 
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,7:  Argumento inválido 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dcahdmi:0,7 
I: [pulseaudio] alsa-util.c: Error opening PCM device dcahdmi:0,7: No  existe el archivo o el directorio 
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2) 
I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No existe el  archivo o el directorio 
I: [pulseaudio] module-card-restore.c: Restoring port latency offsets  for card alsa_card.pci-0000_00_02.0-platform-hdmi-lpe-audio. 
I: [pulseaudio] card.c: Created 0  "alsa_card.pci-0000_00_02.0-platform-hdmi-lpe-audio" 
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0 
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM front:0 
I: [pulseaudio] alsa-util.c: Error opening PCM device front:0: Argumento  inválido 
I: [pulseaudio] alsa-util.c: Trying to disable ALSA period wakeups,  using timers only 
I: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_buffer_size_near()  failed: Argumento inválido 
I: [pulseaudio] alsa-util.c: ALSA period wakeups disabled 
I: [pulseaudio] alsa-sink.c: Successfully opened device hw:0. 
I: [pulseaudio] alsa-sink.c: Selected mapping 'Estéreo analógico'  (analog-stereo). 
I: [pulseaudio] alsa-sink.c: Successfully enabled mmap() mode. 
I: [pulseaudio] alsa-sink.c: Successfully enabled timer-based scheduling  mode. 
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0' 
I: [pulseaudio] sink.c: Created sink 0  "alsa_output.pci-0000_00_02.0-platform-hdmi-lpe-audio.analog-stereo"  with sample spec s16le 2ch 44100Hz and channel map front-left,front-right 
I: [pulseaudio] sink.c:     alsa.resolution_bits = "16" 
I: [pulseaudio] sink.c:     device.api = "alsa" 
I: [pulseaudio] sink.c:     device.class = "sound" 
I: [pulseaudio] sink.c:     alsa.class = "generic" 
I: [pulseaudio] sink.c:     alsa.subclass = "generic-mix" 
I: [pulseaudio] sink.c:     alsa.name = "Intel HDMI/DP LPE Audio" 
I: [pulseaudio] sink.c:     alsa.id = "HdmiLpeAudio" 
I: [pulseaudio] sink.c:     alsa.subdevice = "0" 
I: [pulseaudio] sink.c:     alsa.subdevice_name = "subdevice #0" 
I: [pulseaudio] sink.c:     alsa.device = "0" 
I: [pulseaudio] sink.c:     alsa.card = "0" 
I: [pulseaudio] sink.c:     alsa.card_name = "Intel HDMI/DP LPE Audio" 
I: [pulseaudio] sink.c:     alsa.long_card_name = "Intel HDMI/DP LPE Audio" 
I: [pulseaudio] sink.c:     alsa.driver_name = "snd_hdmi_lpe_audio" 
I: [pulseaudio] sink.c:     device.bus_path =  "pci-0000:00:02.0-platform-hdmi-lpe-audio" 
I: [pulseaudio] sink.c:     sysfs.path =  "/devices/pci0000:00/0000:00:02.0/hdmi-lpe-audio/sound/card0" 
I: [pulseaudio] sink.c:     device.bus = "pci" 
I: [pulseaudio] sink.c:     device.vendor.id = "8086" 
I: [pulseaudio] sink.c:     device.vendor.name = "Intel Corporation" 
I: [pulseaudio] sink.c:     device.product.id = "0f31" 
I: [pulseaudio] sink.c:     device.product.name = "Atom Processor  Z36xxx/Z37xxx Series Graphics & Display" 
I: [pulseaudio] sink.c:     device.string = "hw:0" 
I: [pulseaudio] sink.c:     device.buffering.buffer_size = "352832" 
I: [pulseaudio] sink.c:     device.buffering.fragment_size = "352832" 
I: [pulseaudio] sink.c:     device.access_mode = "mmap+timer" 
I: [pulseaudio] sink.c:     device.profile.name = "analog-stereo" 
I: [pulseaudio] sink.c:     device.profile.description = "Estéreo analógico" 
I: [pulseaudio] sink.c:     device.description = "Atom Processor  Z36xxx/Z37xxx Series Graphics & Display Estéreo analógico" 
I: [pulseaudio] sink.c:     module-udev-detect.discovered = "1" 
I: [pulseaudio] sink.c:     device.icon_name = "audio-card-pci" 
I: [pulseaudio] source.c: Created source 0  "alsa_output.pci-0000_00_02.0-platform-hdmi-lpe-audio.analog-stereo.monitor"  with sample spec s16le 2ch 44100Hz and channel map front-left,front-right 
I: [pulseaudio] source.c:     device.description = "Monitor of Atom  Processor Z36xxx/Z37xxx Series Graphics & Display Estéreo analógico" 
I: [pulseaudio] source.c:     device.class = "monitor" 
I: [pulseaudio] source.c:     alsa.card = "0" 
I: [pulseaudio] source.c:     alsa.card_name = "Intel HDMI/DP LPE Audio" 
I: [pulseaudio] source.c:     alsa.long_card_name = "Intel HDMI/DP LPE  Audio" 
I: [pulseaudio] source.c:     alsa.driver_name = "snd_hdmi_lpe_audio" 
I: [pulseaudio] source.c:     device.bus_path =  "pci-0000:00:02.0-platform-hdmi-lpe-audio" 
I: [pulseaudio] source.c:     sysfs.path =  "/devices/pci0000:00/0000:00:02.0/hdmi-lpe-audio/sound/card0" 
I: [pulseaudio] source.c:     device.bus = "pci" 
I: [pulseaudio] source.c:     device.vendor.id = "8086" 
I: [pulseaudio] source.c:     device.vendor.name = "Intel Corporation" 
I: [pulseaudio] source.c:     device.product.id = "0f31" 
I: [pulseaudio] source.c:     device.product.name = "Atom Processor  Z36xxx/Z37xxx Series Graphics & Display" 
I: [pulseaudio] source.c:     device.string = "0" 
I: [pulseaudio] source.c:     module-udev-detect.discovered = "1" 
I: [pulseaudio] source.c:     device.icon_name = "audio-card-pci" 
I: [pulseaudio] alsa-sink.c: Using 1,0 fragments of size 352832 bytes  (2000,18ms), buffer size is 352832 bytes (2000,18ms) 
I: [pulseaudio] alsa-sink.c: Time scheduling watermark is 20,00ms 
I: [pulseaudio] alsa-sink.c: Driver does not support hardware volume  control, falling back to software volume control. 
I: [pulseaudio] alsa-sink.c: Driver does not support hardware mute  control, falling back to software mute control. 
I: [alsa-sink-HdmiLpeAudio] core-util.c: Successfully enabled SCHED_RR  scheduling for thread, with priority 5. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] (alsa-lib)pcm_hw.c: SNDRV_PCM_IOCTL_HWSYNC  failed (-32) 
I: [pulseaudio] module.c: Loaded "module-alsa-card" (index: #6;  argument: "device_id="0" name="pci-0000_00_02.0-platform-hdmi-lpe-audio"  card_name="alsa_card.pci-0000_00_02.0-platform-hdmi-lpe-audio"  namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no  deferred_volume=yes use_ucm=yes  card_properties="module-udev-detect.discovered=1""). 
I: [pulseaudio] module-udev-detect.c: Card  /devices/pci0000:00/0000:00:02.0/hdmi-lpe-audio/sound/card0  (alsa_card.pci-0000_00_02.0-platform-hdmi-lpe-audio) module loaded. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [pulseaudio] alsa-ucm.c: UCM available for card chtrt5645 
I: [pulseaudio] alsa-ucm.c: Set UCM verb to HiFi 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [pulseaudio] module-alsa-card.c: Found UCM profiles 
I: [pulseaudio] module-card-restore.c: Restoring port latency offsets  for card alsa_card.platform-cht-bsw-rt5645. 
I: [pulseaudio] card.c: Created 1 "alsa_card.platform-cht-bsw-rt5645" 
I: [pulseaudio] alsa-ucm.c: Set UCM verb to HiFi 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [pulseaudio] alsa-util.c: Cannot disable ALSA period wakeups 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
I: [alsa-sink-HdmiLpeAudio] alsa-sink.c: Starting playback. 
Terminado (killed) 




And i would want can fix this problem please help, 
Sorry my english is nor very good. 

Very thanks. 

[/I][/I][/I][/I][/FONT]

---

### Post by ambrop7 on 2017-08-12
Hi,
I have found the solution which makes audio work on my T102HA. The problem is actually in the HDMI audio driver and it can be worked around by preventing that driver from loading.
This should be doable by adding the following like to /etc/modprobe.d/blacklist.conf:
blacklist snd_hdmi_lpe_audio

Once you have that reboot and verify that module snd_hdmi_lpe_audio is not loaded (lsmod |grep snd_hdmi_lpe_audio) (if it is then find a working approach to blacklist it, I don't have Ubuntu actually). After you get it to not load, pulseaudio should run without crashing and audio should work. You may need to use pavucontrol to select speakers instead of headphones.

---

