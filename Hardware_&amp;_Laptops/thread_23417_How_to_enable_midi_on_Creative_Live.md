---
title: "How to enable midi on Creative Live?"
date: 2005-04-01
forum: Hardware &amp; Laptops
---

### Post by drasko on 2005-04-01
I was trying and trying... I can not hear midi, not from Muse, nor from playmidi. Playmidi says: no device found...  But gnome sees my creative ok, and so does Jack (I hope)...  can some one explain this to me? I want to use Creative's synth, and not virtual synth...  aconnect -o gives me:

client 64: 'EMU10K1 MPU-401 (UART) - Rawmidi 0' [type=kernel]
    0 'EMU10K1 MPU-401 (UART)'
client 65: 'Emu10k1 WaveTable' [type=kernel]
    0 'Emu10k1 Port 0  '
    1 'Emu10k1 Port 1  '
    2 'Emu10k1 Port 2  '
    3 'Emu10k1 Port 3  '
client 72: 'Virtual Raw MIDI 1-0' [type=kernel]
    0 'VirMIDI 1-0     '
client 73: 'Virtual Raw MIDI 1-1' [type=kernel]
    0 'VirMIDI 1-1     '
client 74: 'Virtual Raw MIDI 1-2' [type=kernel]
    0 'VirMIDI 1-2     '
client 75: 'Virtual Raw MIDI 1-3' [type=kernel]
    0 'VirMIDI 1-3     '

Similar for the inputs... What is the differenc between UART an WaveTable -- what are these? How to connect and what to connect to get sound?

---

### Post by drasko on 2005-05-26
So, theres the story:

I can now with lsmod see this modules:

snd_emu10k1_synth       6656  1
snd_emux_synth         33280  2 snd_emu10k1_synth
snd_seq_virmidi         7296  1 snd_emux_synth
snd_seq_midi_emul       7424  1 snd_emux_synth
snd_seq_midi            8224  0
snd_seq_oss            30080  0
snd_seq_midi_event      7424  3 snd_seq_virmidi,snd_seq_midi,snd_seq_oss
snd_seq                46992  15 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_oss,snd_seq_midi_event

etc...

If they are not there try modprobeing them.

I had a problem with snd-seq, so qjackctl would not open... I modprobed this, now it opens ok.

I did apt-get awesfx, and did asfxload myfile.sf.

Now in Muse, i go to the config-midi pull down menu and choose not emu UART, but emu port0 and it works!

Good thing, so read [http://ubuntuforums.org/showthread.php?t=8736&highlight=midi+creative+live](http://ubuntuforums.org/showthread.php?t=8736&highlight=midi+creative+live)

Thanks all.

Drasko

---

