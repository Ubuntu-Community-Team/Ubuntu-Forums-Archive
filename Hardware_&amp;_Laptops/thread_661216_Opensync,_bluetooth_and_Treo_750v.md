---
title: "Opensync, bluetooth and Treo 750v"
date: 2008-01-07
forum: Hardware &amp; Laptops
---

### Post by lgambett on 2008-01-07
Hello to everyone,
I have managed successfully to connect via Bluetooth my Treo 750v running WM6 with my Kubuntu 7.10 Gutsy linux box. I managed also to synchronize files between the PC and the Treo.
I have compiled from source the following;

- libopensync 0.22
- libopensync-plugin-kdepim 0.22
- libopensync-plugin-phyton 0.22
- msynctool 0.22

- librapi2 0.10
- librtfcomp 1.1
- libsynce 0.10
- odccm 0.10
- pywbxml 0.10
- synce-rra 0.10
- synce-sync-engine 0.10
- wbxml2-0.9.2+svn49synce

Happy for the first successes I decided to compile - libopensync-plugin-synce 0.22 in order to sync kontact with the PDA, but.... ./configure halts with 
configure: error: Can't find RRA library
but librra is present and installed in /usr/local/lib... How can I fix this problem ?

Thanks !
Luca

---

