---
title: "Dual Sound Card Issues"
date: 2009-02-21
forum: Hardware
---

### Post by jyaan on 2009-02-21
I have two sound cards, and would like to have playback from both.

These are the two sound cards : ```
$ lspci|grep -i aud
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
01:08.0 Multimedia audio controller: Creative Labs SB Audigy LS

``` The nVidia card is on-board, and the SB Audigy is PCI. I currently use SB Audigy for all of my sound output.

When I go to System->Preferences->Sound, I have only managed to get audio from the on-board card by selecting it explicitly w/ OSS output (eg. selecting 'HDA NVidia ALC662 Analog OSS'). Selecting 'PulseAudio Sound Server' gives only output on Audigy. Before I bought my Audigy, the on-board sound worked fine (although there was some nasty static sound w/ all playback).

How can I get both cards to simultaneously output sound?

---

### Post by jyaan on 2009-02-25
I still haven't managed to find a solution. Any advice would be appreciated, thank you.

---

### Post by jyaan on 2009-03-15
Never did solve this =/

---

