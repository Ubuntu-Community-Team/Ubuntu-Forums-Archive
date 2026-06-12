---
title: "Ubuntu 15.10 doesn't like my Behringer 302USB Mixer"
date: 2015-12-07
forum: Hardware
---

### Post by commodore256 on 2015-12-07
Edit: It's a 302, not a 502

It records too fast and I've googled it and google doesn't always work for everybody. (It works fine for my webcam mic)


```
~$ audacity 
ALSA lib pcm.c:2267:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2267:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2267:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm_route.c:867:(find_matching_chmap) Found no matching channel map
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
14:52:11: Debug: DirManager: Created new instance.
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4611
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4611
Expression 'ret' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1736
Expression 'AlsaOpen( &alsaApi->baseHostApiRep, params, streamDir, &self->pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1904
Expression 'PaAlsaStreamComponent_Initialize( &self->capture, alsaApi, inParams, StreamDirection_In, NULL != callback )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2171
Expression 'PaAlsaStream_Initialize( stream, alsaHostApi, inputParameters, outputParameters, sampleRate, framesPerBuffer, callback, streamFlags, userData )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2840
14:52:12: Debug: PortAudio stream error creating device list: ALSA:USB Audio CODEC: - (hw:1,0): Device unavailable
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4611
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4611
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4611
14:52:22: Debug: AudioIO::GetBestRate() for capture
14:52:22: Debug: GetBestRate() suggested rate 48000 Hz
14:52:22: Debug: GetBestRate() Returning 48000 Hz

```

---

### Post by commodore256 on 2015-12-12
](*,)

---

