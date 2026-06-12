---
title: "Brasero and Lite-On SHW-160P6S"
date: 2009-03-20
forum: Hardware
---

### Post by slightlystoopid on 2009-03-20
when I try to burn a divx or avi movie to a dvd with brasero, it gives me the following error: It is not possible to write with the current set of plugins. I'm not sure if brasero is just not capable of converting avi and divx to iso or what. I saw in another post that someone else solved the problem by switching to ahci mode in their bios, but I was already there. this is the output of brasero --debug:
```
(brasero:6530): BraseroBurn-DEBUG: At burn-basics.c:94: Initializing Brasero-0.9.1
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:429: opening plugin directory /usr/lib/brasero/plugins
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-local-track.so
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3078: New caps required Image BIN CUE CDRDAO CLONE format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3138: Created new caps Image BIN CUE CDRDAO CLONE 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3157: New caps required Audio RAW AUDIO UNDEFINED 4 CHANNELS MP2 AC3 44100 48000 VIDEO UNDEFINED VCD Video DVD Metadata Information format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3245: Created new caps Audio RAW AUDIO UNDEFINED 4 CHANNELS MP2 AC3 44100 48000 VIDEO UNDEFINED VCD Video DVD Metadata Information 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3157: New caps required Audio RAW AUDIO UNDEFINED 4 CHANNELS MP2 AC3 44100 48000 VIDEO UNDEFINED VCD Video DVD format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3245: Created new caps Audio RAW AUDIO UNDEFINED 4 CHANNELS MP2 AC3 44100 48000 VIDEO UNDEFINED VCD Video DVD 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3264: New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1005: Module File Downloader successfully loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-checksum.so
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3078: New caps required Image BIN format accepts files pipe 
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1005: Module Image Checksum successfully loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-dvdauthor.so
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1001: Module encountered an error while registering its capabilities:
"dvdauthor" could not be found in the path
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:479: Load failure, no GType was returned "dvdauthor" could not be found in the path
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-readcd.so
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1001: Module encountered an error while registering its capabilities:
"readcd" could not be found in the path
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:479: Load failure, no GType was returned "readcd" could not be found in the path
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-readom.so
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3078: New caps required Image CLONE format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD W appendable with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD W appendable with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD W closed with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD W closed with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD RW appendable with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD RW appendable with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD RW closed with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD RW closed with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD ROM closed with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD ROM closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD ROM closed with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3078: New caps required Image BIN format accepts files pipe 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD DL ROM closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD ROM closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD DL + W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD DL + W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD DL + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD + W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD + W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD - (restricted) RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD DL - (sequential) W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD DL - (sequential) W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD - (sequential) W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD - (sequential) W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD - (sequential) RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD - (sequential) RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD ROM closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1005: Module readom successfully loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-genisoimage.so
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3264: New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3078: New caps required Image BIN format accepts files pipe 
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1005: Module genisoimage successfully loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-checksum-file.so
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3264: New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL + W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL + W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (restricted) RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL - (sequential) W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL - (sequential) W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1005: Module File Checksum successfully loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-normalize.so
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3157: New caps required Audio AUDIO UNDEFINED Metadata Information format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3245: Created new caps Audio AUDIO UNDEFINED Metadata Information 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3157: New caps required Audio AUDIO UNDEFINED format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3245: Created new caps Audio AUDIO UNDEFINED 
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1005: Module Normalize successfully loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-transcode.so
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3157: New caps required Audio RAW 44100 Metadata Information format accepts files pipe 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3245: Created new caps Audio RAW 44100 Metadata Information 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3157: New caps required Audio AUDIO UNDEFINED Metadata Information format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3157: New caps required Audio RAW 44100 format accepts files pipe 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3245: Created new caps Audio RAW 44100 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3157: New caps required Audio AUDIO UNDEFINED format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1005: Module transcode successfully loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-cdrdao.so
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD W appendable with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD W appendable with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD W closed with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD W closed with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW appendable with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW appendable with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW closed with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW closed with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD ROM closed with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD ROM closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD ROM closed with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3078: New caps required Image CDRDAO format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc CD RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3078: New caps required Image CUE CDRDAO format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW appendable with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW appendable with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW closed with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW closed with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc CD RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc CD RW closed with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc CD RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc CD RW closed with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc CD RW appendable with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc CD RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc CD RW appendable with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1005: Module Cdrdao successfully loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-growisofs.so
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3078: New caps required Image BIN format accepts files pipe 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc BD DL POW W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc BD POW W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc BD DL SRM W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc BD SRM W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD DL + W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD + W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD DL - (sequential) W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD - (sequential) W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD DL - (jump) W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD - (sequential) RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD - (sequential) RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc BD DL RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc BD DL RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc BD DL RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc BD RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc BD RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc BD RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD RAM RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD RAM RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD DL + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD DL + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (restricted) RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD - (restricted) RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD - (restricted) RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3264: New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc BD DL RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc BD DL RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc BD RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc BD RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc BD DL POW W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc BD DL POW W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc BD POW W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc BD POW W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc BD DL SRM W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc BD DL SRM W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc BD SRM W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc BD SRM W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD RAM RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL + W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL + W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (restricted) RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (restricted) RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL - (sequential) W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL - (sequential) W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3357: Created Disc DVD DL - (jump) W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL - (jump) W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc BD DL RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc BD RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD RAM RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (restricted) RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (restricted) RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (restricted) RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (restricted) RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD - (restricted) RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD - (restricted) RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD - (restricted) RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD DL + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD DL + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD DL + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1005: Module growisofs successfully loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-cdrecord.so
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1001: Module encountered an error while registering its capabilities:
"cdrecord" is a symlink pointing to another program. Use the target program instead
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:479: Load failure, no GType was returned "cdrecord" is a symlink pointing to another program. Use the target program instead
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-toc2cue.so
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3078: New caps required Image CDRDAO format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3078: New caps required Image CUE format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1005: Module toc2cue successfully loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-vcdimager.so
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1001: Module encountered an error while registering its capabilities:
"vcdimager" could not be found in the path
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:479: Load failure, no GType was returned "vcdimager" could not be found in the path
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-vob.so
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1001: Module encountered an error while registering its capabilities:
unknown error
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:479: Load failure, no GType was returned (null)
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-mkisofs.so
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1001: Module encountered an error while registering its capabilities:
"mkisofs" is a symlink pointing to another program. Use the target program instead
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:479: Load failure, no GType was returned "mkisofs" is a symlink pointing to another program. Use the target program instead
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-burn-uri.so
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3078: New caps required Image BIN CUE CDRDAO CLONE format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3264: New caps required Data ISO UDF Level 3 JOLIET VIDEO DEEP 
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1005: Module CD/DVD Creator Folder successfully loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-wodim.so
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3078: New caps required Image BIN format accepts files pipe 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD W appendable with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD W appendable with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW appendable with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW appendable with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3157: New caps required Audio RAW 44100 Metadata Information format accepts files pipe 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3157: New caps required Audio RAW 44100 format accepts files pipe 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3078: New caps required Image CUE CLONE format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW appendable with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW appendable with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW closed with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW closed with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc CD RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc CD RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc CD RW closed with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc CD RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc CD RW closed with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc CD RW appendable with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc CD RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc CD RW appendable with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1005: Module wodim successfully loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-dvdcss.so
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1001: Module encountered an error while registering its capabilities:
Encrypted DVD: please, install libdvdcss version 1.2.x
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:479: Load failure, no GType was returned Encrypted DVD: please, install libdvdcss version 1.2.x
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:451: loading /usr/lib/brasero/plugins/libbrasero-dvdrwformat.so
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (restricted) RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (restricted) RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (restricted) RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL - (sequential) W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL - (sequential) W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD DL - (sequential) W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3345: Retrieved Disc DVD - (sequential) RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD - (sequential) RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD - (sequential) RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD - (sequential) RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD - (sequential) RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD DL - (sequential) W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD DL - (sequential) W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD DL - (sequential) W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD - (restricted) RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD - (restricted) RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD - (restricted) RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD DL + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD DL + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3459: Adding blank caps for Disc DVD DL + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:1005: Module dvd+rw-format successfully loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:146: Getting list of plugins to be loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:146: Plugin dvd+rw-format is active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:305: Watching GConf plugin key
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin dvd+rw-format active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:146: Plugin wodim is active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:305: Watching GConf plugin key
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin wodim active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:146: Plugin CD/DVD Creator Folder is active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:227: Setting plugin CD/DVD Creator Folder active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:146: Plugin toc2cue is active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:305: Watching GConf plugin key
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin toc2cue active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:146: Plugin growisofs is active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:305: Watching GConf plugin key
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin growisofs active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:146: Plugin Cdrdao is active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:305: Watching GConf plugin key
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin Cdrdao active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:146: Plugin transcode is active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:305: Watching GConf plugin key
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin transcode active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:146: Plugin Normalize is active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:227: Setting plugin Normalize active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:146: Plugin File Checksum is active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:227: Setting plugin File Checksum active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:146: Plugin genisoimage is active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:305: Watching GConf plugin key
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin genisoimage active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin.c:146: Plugin readom is active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:305: Watching GConf plugin key
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin readom active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:227: Setting plugin Image Checksum inactive
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:227: Setting plugin File Downloader inactive
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:235: Watching GConf plugin key
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 1 links pointing to Disc DVD DL - (jump) W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 1 links pointing to Disc BD SRM W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 1 links pointing to Disc BD DL SRM W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 1 links pointing to Disc BD POW W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 1 links pointing to Disc BD DL POW W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc DVD - (restricted) RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc DVD - (restricted) RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc DVD + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc DVD + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc DVD DL + RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc DVD DL + RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc DVD RAM RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc DVD RAM RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc BD RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc BD RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc BD RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc BD DL RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc BD DL RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc BD DL RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc DVD - (sequential) RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc DVD - (sequential) RW blank Unformatted 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc DVD DL - (jump) W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc DVD - (sequential) W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc DVD DL - (sequential) W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc DVD + W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc DVD DL + W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc BD SRM W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc BD DL SRM W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc BD POW W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc BD DL POW W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 23 links pointing to Disc CD RW blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 22 links pointing to Disc CD W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 1 links pointing to Disc CD RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 1 links pointing to Disc CD RW closed with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 1 links pointing to Disc CD RW closed with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 5 links pointing to Disc CD RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 5 links pointing to Disc CD RW appendable with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 5 links pointing to Disc CD RW appendable with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Disc CD W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Disc CD W closed with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Disc CD W closed with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc CD W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc CD W appendable with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc CD W appendable with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Disc CD ROM closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Disc CD ROM closed with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Disc CD ROM closed with data with audio 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Disc DVD ROM closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc DVD + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Disc DVD + W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc DVD + W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 1 links pointing to Disc DVD - (sequential) RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc DVD - (sequential) RW appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Disc DVD - (sequential) W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 3 links pointing to Disc DVD - (sequential) W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc DVD - (restricted) RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Disc DVD DL ROM closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 4 links pointing to Disc DVD DL + RW closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Disc DVD DL + W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 1 links pointing to Disc DVD DL + W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 1 links pointing to Disc DVD DL - (sequential) W closed with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 2 links pointing to Disc DVD DL - (sequential) W appendable with data 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 21 links pointing to Image BIN format accepts pipe 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 21 links pointing to Image BIN format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 1 links pointing to Image CUE format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 15 links pointing to Image CLONE format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 15 links pointing to Image CDRDAO format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Data ISO UDF Level 3 JOLIET VIDEO DEEP 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Audio AUDIO UNDEFINED format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 1 links pointing to Audio RAW 44100 format accepts files pipe 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Audio RAW AUDIO UNDEFINED 4 CHANNELS MP2 AC3 44100 48000 VIDEO UNDEFINED VCD Video DVD format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Audio AUDIO UNDEFINED Metadata Information format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 1 links pointing to Audio RAW 44100 Metadata Information format accepts files pipe 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3845: Created 0 links pointing to Audio RAW AUDIO UNDEFINED 4 CHANNELS MP2 AC3 44100 48000 VIDEO UNDEFINED VCD Video DVD Metadata Information format accepts files 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:3735: checking media caps for Disc DVD + W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:146: Getting list of plugins to be loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin dvd+rw-format active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin wodim active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:227: Setting plugin CD/DVD Creator Folder active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin toc2cue active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin growisofs active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin Cdrdao active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin transcode active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:227: Setting plugin Normalize active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:227: Setting plugin File Checksum active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin genisoimage active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin readom active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:227: Setting plugin Image Checksum inactive
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:227: Setting plugin File Downloader inactive
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:235: Watching GConf plugin key
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:146: Getting list of plugins to be loaded
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin dvd+rw-format active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin wodim active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:227: Setting plugin CD/DVD Creator Folder active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin toc2cue active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin growisofs active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin Cdrdao active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin transcode active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:227: Setting plugin Normalize active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:227: Setting plugin File Checksum active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin genisoimage active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:195: Setting plugin readom active
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:227: Setting plugin Image Checksum inactive
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:227: Setting plugin File Downloader inactive
(brasero:6530): BraseroBurn-DEBUG: At burn-plugin-manager.c:235: Watching GConf plugin key
(brasero:6530): BraseroBurn-DEBUG: At brasero-io.c:940: Retrieving metadata info
(brasero:6530): BraseroBurn-DEBUG: At brasero-io.c:792: Retrieving available metadata file:///home/jschmidt/large/Movies/fear%20and%20loathing%20in%20las%20vegas.divx
(brasero:6530): BraseroBurn-DEBUG: At brasero-metadata.c:1387: New retrieval for file:///home/jschmidt/large/Movies/fear%20and%20loathing%20in%20las%20vegas.divx 0x26ae1a0
(brasero:6530): BraseroBurn-DEBUG: At brasero-metadata.c:1249: New pad for file:///home/jschmidt/large/Movies/fear%20and%20loathing%20in%20las%20vegas.divx
(brasero:6530): BraseroBurn-DEBUG: At brasero-metadata.c:1278: RAW video stream found
(brasero:6530): BraseroBurn-DEBUG: At brasero-metadata.c:1204: Linking to a fake sink
(brasero:6530): BraseroBurn-DEBUG: At brasero-metadata.c:1554: Metadata lock and wait 0x26ae1a0
(brasero:6530): BraseroBurn-DEBUG: At brasero-metadata.c:1032: State changed to PAUSED or PLAYING
(brasero:6530): BraseroBurn-DEBUG: At brasero-metadata.c:574: Metadata retrieval successfully completed for file:///home/jschmidt/large/Movies/fear%20and%20loathing%20in%20las%20vegas.divx
(brasero:6530): BraseroBurn-DEBUG: At brasero-metadata.c:606: found duration 7105842612285 for file:///home/jschmidt/large/Movies/fear%20and%20loathing%20in%20las%20vegas.divx
(brasero:6530): BraseroBurn-DEBUG: At brasero-metadata.c:255: Retrieval ended for file:///home/jschmidt/large/Movies/fear%20and%20loathing%20in%20las%20vegas.divx 0x26ae1a0
(brasero:6530): BraseroBurn-DEBUG: At brasero-io.c:902: Stopping metadata information retrieval (0x26ae1a0)
(brasero:6530): BraseroBurn-DEBUG: At brasero-metadata.c:319: Metadata retrieval cancelled for file:///home/jschmidt/large/Movies/fear%20and%20loathing%20in%20las%20vegas.divx 0x26ae1a0
(brasero:6530): BraseroBurn-DEBUG: At brasero-metadata.c:255: Retrieval ended for file:///home/jschmidt/large/Movies/fear%20and%20loathing%20in%20las%20vegas.divx 0x26ae1a0
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:2040: Checking support for session output Disc DVD + W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:2041: and input Audio AUDIO UNDEFINED VIDEO UNDEFINED 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:1649: find_link Disc DVD + W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:1649: find_link Data ISO UDF Level 3 JOLIET VIDEO DEEP 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:1649: find_link Image BIN 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:1649: find_link Data ISO UDF Level 3 JOLIET VIDEO DEEP 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:1787: Support for input/output failed.
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:586: Testing blanking caps for Disc DVD + W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:525: Testing blanking caps for Disc DVD + W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:542: Searching links for caps Disc DVD + W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:542: Searching links for caps Disc DVD DL + W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:573: No blanking capabilities for Disc DVD + W blank 
(brasero:6530): BraseroBurn-DEBUG: At burn-caps.c:2053: Output not supported Disc DVD + W blank 
```

---

### Post by williambertram on 2009-04-27
Getting same thing.  Mine is a Lite-On LH-20A1H.

---

