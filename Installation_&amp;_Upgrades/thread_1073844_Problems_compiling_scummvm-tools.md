---
title: "Problems compiling scummvm-tools"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by chris_ka on 2009-02-18
Hello,

In order to play Floyd (German version of "The Feeble Files") I'm following the howoto on [http://wiki.ubuntuusers.de/Spiele/Floyd](http://wiki.ubuntuusers.de/Spiele/Floyd), which requires to install "scummvm-tools", among other stuff.

Trying to start compiling the source code of scummvm-tools with "./make" I' shown the error message, pasted below.
(unfortunately I'm running my system in German - which might complicate helping me, nevertheless any hint is appreciated:)

Thanks,
Chris

###############
mkdir -p ./.deps
g++ -Wp,-MMD,"./.deps/compress.d",-MQ,"compress.o",-MP -Wall -g -O -Wuninitialized -Wno-long-long -Wno-multichar -Wno-unknown-pragmas -Wno-reorder -Wpointer-arith -Wcast-qual -Wconversion -Wshadow -Wimplicit -Wundef -Wnon-virtual-dtor -Wwrite-strings -fno-exceptions -fcheck-new -DUNIX -I. -I. -c compress.cpp -o compress.o
In file included from compress.cpp:23:
compress.h:27:30: warning: vorbis/vorbisenc.h: No such file or directory
compress.h:28:33: warning: FLAC/stream_encoder.h: No such file or directory
In file included from compress.h:26,
                 from compress.cpp:23:
util.h: In function »uint16 SWAP_16(uint16)«:
util.h:126: Warnung: Umwandlung in »uint16« von »int« könnte den Wert ändern
util.h: In function »uint16 READ_LE_UINT16(const void*)«:
util.h:133: Warnung: Umwandlung in »uint16« von »int« könnte den Wert ändern
util.h: In function »uint16 READ_BE_UINT16(const void*)«:
util.h:154: Warnung: Umwandlung in »uint16« von »int« könnte den Wert ändern
compress.cpp: In function »void encodeAudio(const char*, bool, int, const char*, CompressMode)«:
compress.cpp:289: Warnung: Umwandlung in »uint8« von »int« könnte den Wert ändern
compress.cpp:248: Warnung: Der Rückgabewert von »size_t fread(void*, size_t, size_t, FILE*)«, der mit dem Attribut warn_unused_result deklariert wurde, wird ignoriert
compress.cpp:282: Warnung: Der Rückgabewert von »size_t fread(void*, size_t, size_t, FILE*)«, der mit dem Attribut warn_unused_result deklariert wurde, wird ignoriert
compress.cpp: In function »void encodeRaw(char*, int, int, const char*, CompressMode)«:
compress.cpp:308: Fehler: »vorbis_info« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:308: Fehler: expected `;' before »vi«
compress.cpp:309: Fehler: »vorbis_comment« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:309: Fehler: expected `;' before »vc«
compress.cpp:310: Fehler: »vorbis_dsp_state« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:310: Fehler: expected `;' before »vd«
compress.cpp:311: Fehler: »vorbis_block« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:311: Fehler: expected `;' before »vb«
compress.cpp:313: Fehler: »ogg_stream_state« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:313: Fehler: expected `;' before »os«
compress.cpp:314: Fehler: »ogg_page« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:314: Fehler: expected `;' before »og«
compress.cpp:315: Fehler: »ogg_packet« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:315: Fehler: expected `;' before »op«
compress.cpp:317: Fehler: expected `;' before »header«
compress.cpp:318: Fehler: expected `;' before »header_comm«
compress.cpp:319: Fehler: expected `;' before »header_code«
compress.cpp:323: Fehler: »vi« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:323: Fehler: »vorbis_info_init« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:329: Fehler: »vorbis_encode_setup_managed« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:331: Fehler: »OV_EFAULT« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:333: Fehler: »vorbis_info_clear« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:335: Fehler: »OV_EINVAL« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:335: Fehler: »OV_EIMPL« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:337: Fehler: »vorbis_info_clear« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:360: Fehler: »vorbis_encode_setup_vbr« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:362: Fehler: »OV_EFAULT« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:364: Fehler: »vorbis_info_clear« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:366: Fehler: »OV_EINVAL« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:366: Fehler: »OV_EIMPL« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:368: Fehler: »vorbis_info_clear« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:377: Fehler: Aggregat »ovectl_ratemanage_arg extraParam« hat unvollständigen Typ und kann nicht definiert werden
compress.cpp:378: Fehler: »OV_ECTL_RATEMANAGE_GET« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:378: Fehler: »vorbis_encode_ctl« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:384: Fehler: »OV_ECTL_RATEMANAGE_SET« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:406: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente
compress.cpp:408: Fehler: »vorbis_encode_setup_init« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:409: Fehler: »vc« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:409: Fehler: »vorbis_comment_init« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:410: Fehler: »vd« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:410: Fehler: »vorbis_analysis_init« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:411: Fehler: »vb« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:411: Fehler: »vorbis_block_init« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:412: Fehler: »os« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:412: Fehler: »ogg_stream_init« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:413: Fehler: »header« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:413: Fehler: »header_comm« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:413: Fehler: »header_code« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:413: Fehler: »vorbis_analysis_headerout« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:415: Fehler: »ogg_stream_packetin« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:420: Fehler: »og« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:420: Fehler: »ogg_stream_flush« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:433: Fehler: »vorbis_analysis_buffer« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:437: Fehler: »vorbis_analysis_wrote« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:444: Warnung: Umwandlung in »float« von »int« könnte den Wert ändern
compress.cpp:451: Warnung: Umwandlung in »float« von »int« könnte den Wert ändern
compress.cpp:458: Warnung: Umwandlung in »float« von »int« könnte den Wert ändern
compress.cpp:464: Fehler: »vorbis_analysis_wrote« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:467: Fehler: »vorbis_analysis_blockout« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:468: Fehler: »vorbis_analysis« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:469: Fehler: »vorbis_bitrate_addblock« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:471: Fehler: »op« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:471: Fehler: »vorbis_bitrate_flushpacket« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:475: Fehler: »og« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:475: Fehler: »ogg_stream_pageout« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:484: Fehler: »ogg_page_eos« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:495: Fehler: »ogg_stream_clear« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:496: Fehler: »vorbis_block_clear« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:497: Fehler: »vorbis_dsp_clear« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:498: Fehler: »vorbis_info_clear« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:515: Fehler: »FLAC__StreamEncoder« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:515: Fehler: »encoder« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:516: Fehler: »FLAC__StreamEncoderInitStatus« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:516: Fehler: expected `;' before »initStatus«
compress.cpp:517: Fehler: »FLAC__int32« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:517: Fehler: »flacData« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:519: Fehler: expected primary-expression before »)« token
compress.cpp:519: Fehler: expected `;' before »malloc«
compress.cpp:523: Fehler: »FLAC__uint8« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:523: Fehler: »rawDataUnsigned« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:524: Fehler: expected primary-expression before »)« token
compress.cpp:524: Fehler: expected `;' before »rawData«
compress.cpp:525: Fehler: expected `;' before »rawDataUnsigned«
compress.cpp:529: Fehler: »FLAC__int16« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:529: Fehler: »rawData16« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:530: Fehler: expected primary-expression before »)« token
compress.cpp:530: Fehler: expected `;' before »rawData«
compress.cpp:532: Fehler: expected `;' before »rawData16«
compress.cpp:540: Fehler: »FLAC__stream_encoder_new« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:542: Fehler: »FLAC__stream_encoder_set_bits_per_sample« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:543: Fehler: »FLAC__stream_encoder_set_blocksize« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:544: Fehler: »FLAC__stream_encoder_set_channels« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:545: Fehler: »FLAC__stream_encoder_set_compression_level« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:546: Fehler: »FLAC__stream_encoder_set_sample_rate« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:547: Fehler: »FLAC__stream_encoder_set_streamable_subset« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:548: Fehler: »FLAC__stream_encoder_set_total_samples_estimate« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:549: Fehler: »FLAC__stream_encoder_set_verify« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:551: Fehler: »initStatus« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:551: Fehler: »FLAC__stream_encoder_init_file« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:553: Fehler: »FLAC__STREAM_ENCODER_INIT_STATUS_OK« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:555: Fehler: »FLAC__StreamEncoderInitStatusString« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:558: Fehler: »FLAC__stream_encoder_process_interleaved« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:561: Fehler: »FLAC__stream_encoder_finish« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp:562: Fehler: »FLAC__stream_encoder_delete« wurde in diesem Gültigkeitsbereich nicht definiert
compress.cpp: In function »void extractAndEncodeWAV(const char*, FILE*, CompressMode)«:
compress.cpp:592: Warnung: Der Rückgabewert von »size_t fwrite(const void*, size_t, size_t, FILE*)«, der mit dem Attribut warn_unused_result deklariert wurde, wird ignoriert
compress.cpp: In function »void extractAndEncodeVOC(const char*, FILE*, CompressMode)«:
compress.cpp:672: Warnung: Der Rückgabewert von »size_t fwrite(const void*, size_t, size_t, FILE*)«, der mit dem Attribut warn_unused_result deklariert wurde, wird ignoriert
compress.cpp: In function »int process_ogg_parms(int, char**, int)«:
compress.cpp:819: Warnung: Umwandlung in »float« von »int« könnte den Wert ändern
make: *** [compress.o] Fehler 1

---

### Post by mikewu on 2009-02-18
Not sure if this will fix everything, but you need the two files that the warning specify.

Searching for them returns libflac-dev and libvorbis-dev.

```
$ apt-file search stream_encoder.h
libflac-dev: /usr/include/FLAC/stream_encoder.h
$ apt-file search vorbisenc.h
gstreamer0.10-plugins-base-doc: /usr/share/gtk-doc/html/gst-plugins-base-plugins-0.10/gst-plugins-base-plugins-vorbisenc.html
libvorbis-dev: /usr/include/vorbis/vorbisenc.h
```

Try installing those with apt-get and see if you still get warnings.

---

### Post by chris_ka on 2009-02-19
Great, this (and some more) had to be installed.
Finally it worked ;)

Thanks,
Christian

---

