---
title: "libsndfile-1.0.17$ make errror"
date: 2008-10-12
forum: General Help
---

### Post by bldyman on 2008-10-12
I'm truing to compile libsndfile-1.0.17 to use sooperlooper. the ./config seems to be ok but make:

```
bldyman@franco:~/libsndfile-1.0.17$ make
Making all in man
make[1]: Entering directory `/home/bldyman/libsndfile-1.0.17/man'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/bldyman/libsndfile-1.0.17/man'
Making all in doc
make[1]: Entering directory `/home/bldyman/libsndfile-1.0.17/doc'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/bldyman/libsndfile-1.0.17/doc'
Making all in Win32
make[1]: Entering directory `/home/bldyman/libsndfile-1.0.17/Win32'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/bldyman/libsndfile-1.0.17/Win32'
Making all in Octave
make[1]: Entering directory `/home/bldyman/libsndfile-1.0.17/Octave'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/bldyman/libsndfile-1.0.17/Octave'
Making all in src
make[1]: Entering directory `/home/bldyman/libsndfile-1.0.17/src'
make  all-recursive
make[2]: Entering directory `/home/bldyman/libsndfile-1.0.17/src'
Making all in GSM610
make[3]: Entering directory `/home/bldyman/libsndfile-1.0.17/src/GSM610'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/bldyman/libsndfile-1.0.17/src/GSM610'
Making all in G72x
make[3]: Entering directory `/home/bldyman/libsndfile-1.0.17/src/G72x'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/bldyman/libsndfile-1.0.17/src/G72x'
make[3]: Entering directory `/home/bldyman/libsndfile-1.0.17/src'
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -std=gnu99 -W -Wall -Wdeclaration-after-statement -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Waggregate-return -Wcast-align -Wcast-qual -Wnested-externs -Wshadow -Wbad-function-cast -Wwrite-strings  -pipe  -MT flac.lo -MD -MP -MF ".deps/flac.Tpo" -c -o flac.lo flac.c; \
	then mv -f ".deps/flac.Tpo" ".deps/flac.Plo"; else rm -f ".deps/flac.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -std=gnu99 -W -Wall -Wdeclaration-after-statement -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Waggregate-return -Wcast-align -Wcast-qual -Wnested-externs -Wshadow -Wbad-function-cast -Wwrite-strings -pipe -MT flac.lo -MD -MP -MF .deps/flac.Tpo -c flac.c  -fPIC -DPIC -o .libs/flac.o
flac.c:63: error: expected specifier-qualifier-list before 'FLAC__SeekableStreamDecoder'
flac.c:111: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sf_flac_read_callback'
flac.c:112: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sf_flac_seek_callback'
flac.c:113: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sf_flac_tell_callback'
flac.c:114: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sf_flac_length_callback'
flac.c:115: warning: type defaults to 'int' in declaration of 'FLAC__SeekableStreamDecoder'
flac.c:115: error: expected ';', ',' or ')' before '*' token
flac.c:116: warning: type defaults to 'int' in declaration of 'FLAC__SeekableStreamDecoder'
flac.c:116: error: expected ';', ',' or ')' before '*' token
flac.c:117: warning: type defaults to 'int' in declaration of 'FLAC__SeekableStreamDecoder'
flac.c:117: error: expected ';', ',' or ')' before '*' token
flac.c:118: warning: type defaults to 'int' in declaration of 'FLAC__SeekableStreamDecoder'
flac.c:118: error: expected ';', ',' or ')' before '*' token
flac.c:121: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sf_flac_enc_seek_callback'
flac.c:125: warning: type defaults to 'int' in declaration of 'FLAC__SeekableStreamEncoder'
flac.c:125: error: expected ';', ',' or ')' before '*' token
flac.c: In function 'flac_buffer_copy':
flac.c:171: error: 'FLAC_PRIVATE' has no member named 'frame'
flac.c:172: error: 'FLAC_PRIVATE' has no member named 'wbuffer'
flac.c:175: error: 'FLAC_PRIVATE' has no member named 'ptr'
flac.c:180: error: 'FLAC_PRIVATE' has no member named 'bufferbackup'
flac.c:182: error: 'FLAC_PRIVATE' has no member named 'rbuffer'
flac.c:183: error: 'FLAC_PRIVATE' has no member named 'rbuffer'
flac.c:184: error: 'FLAC_PRIVATE' has no member named 'rbuffer'
flac.c:186: error: 'FLAC_PRIVATE' has no member named 'wbuffer'
flac.c:186: error: 'FLAC_PRIVATE' has no member named 'rbuffer'
flac.c:191: error: 'FLAC_PRIVATE' has no member named 'pcmtype'
flac.c:193: error: 'FLAC_PRIVATE' has no member named 'ptr'
flac.c:197: error: 'FLAC_PRIVATE' has no member named 'remain'
flac.c:198: error: 'FLAC_PRIVATE' has no member named 'pos'
flac.c:200: error: 'FLAC_PRIVATE' has no member named 'bufferpos'
flac.c:201: error: 'FLAC_PRIVATE' has no member named 'remain'
flac.c:202: error: 'FLAC_PRIVATE' has no member named 'bufferpos'
flac.c:206: error: 'FLAC_PRIVATE' has no member named 'remain'
flac.c:207: error: 'FLAC_PRIVATE' has no member named 'pos'
flac.c:209: error: 'FLAC_PRIVATE' has no member named 'bufferpos'
flac.c:213: error: 'FLAC_PRIVATE' has no member named 'bufferpos'
flac.c:215: error: 'FLAC_PRIVATE' has no member named 'remain'
flac.c:216: error: 'FLAC_PRIVATE' has no member named 'bufferpos'
flac.c:223: error: 'FLAC_PRIVATE' has no member named 'ptr'
flac.c:225: error: 'FLAC_PRIVATE' has no member named 'remain'
flac.c:226: error: 'FLAC_PRIVATE' has no member named 'pos'
flac.c:228: error: 'FLAC_PRIVATE' has no member named 'bufferpos'
flac.c:232: error: 'FLAC_PRIVATE' has no member named 'bufferpos'
flac.c:233: error: 'FLAC_PRIVATE' has no member named 'remain'
flac.c:234: error: 'FLAC_PRIVATE' has no member named 'bufferpos'
flac.c:240: error: 'FLAC_PRIVATE' has no member named 'ptr'
flac.c:243: error: 'FLAC_PRIVATE' has no member named 'remain'
flac.c:244: error: 'FLAC_PRIVATE' has no member named 'pos'
flac.c:246: error: 'FLAC_PRIVATE' has no member named 'bufferpos'
flac.c:250: error: 'FLAC_PRIVATE' has no member named 'bufferpos'
flac.c:251: error: 'FLAC_PRIVATE' has no member named 'remain'
flac.c:252: error: 'FLAC_PRIVATE' has no member named 'bufferpos'
flac.c:258: error: 'FLAC_PRIVATE' has no member named 'ptr'
flac.c:261: error: 'FLAC_PRIVATE' has no member named 'remain'
flac.c:262: error: 'FLAC_PRIVATE' has no member named 'pos'
flac.c:264: error: 'FLAC_PRIVATE' has no member named 'bufferpos'
flac.c:268: error: 'FLAC_PRIVATE' has no member named 'bufferpos'
flac.c:269: error: 'FLAC_PRIVATE' has no member named 'remain'
flac.c:270: error: 'FLAC_PRIVATE' has no member named 'bufferpos'
flac.c:280: error: 'FLAC_PRIVATE' has no member named 'pos'
flac.c: At top level:
flac.c:287: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sf_flac_read_callback'
flac.c:298: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sf_flac_seek_callback'
flac.c:309: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sf_flac_tell_callback'
flac.c:320: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sf_flac_length_callback'
flac.c:330: warning: type defaults to 'int' in declaration of 'FLAC__SeekableStreamDecoder'
flac.c:330: error: expected ';', ',' or ')' before '*' token
flac.c:340: warning: type defaults to 'int' in declaration of 'FLAC__SeekableStreamDecoder'
flac.c:340: error: expected ';', ',' or ')' before '*' token
flac.c:356: warning: type defaults to 'int' in declaration of 'FLAC__SeekableStreamDecoder'
flac.c:356: error: expected ';', ',' or ')' before '*' token
flac.c:390: warning: type defaults to 'int' in declaration of 'FLAC__SeekableStreamDecoder'
flac.c:390: error: expected ';', ',' or ')' before '*' token
flac.c:411: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sf_flac_enc_seek_callback'
flac.c:435: warning: type defaults to 'int' in declaration of 'FLAC__SeekableStreamEncoder'
flac.c:435: error: expected ';', ',' or ')' before '*' token
flac.c: In function 'flac_close':
flac.c:512: warning: implicit declaration of function 'FLAC__seekable_stream_encoder_finish'
flac.c:512: warning: nested extern declaration of 'FLAC__seekable_stream_encoder_finish'
flac.c:512: error: 'FLAC_PRIVATE' has no member named 'fse'
flac.c:513: warning: implicit declaration of function 'FLAC__seekable_stream_encoder_delete'
flac.c:513: warning: nested extern declaration of 'FLAC__seekable_stream_encoder_delete'
flac.c:513: error: 'FLAC_PRIVATE' has no member named 'fse'
flac.c:514: error: 'FLAC_PRIVATE' has no member named 'encbuffer'
flac.c:515: error: 'FLAC_PRIVATE' has no member named 'encbuffer'
flac.c:519: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_finish'
flac.c:519: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_finish'
flac.c:519: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:520: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_delete'
flac.c:520: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_delete'
flac.c:520: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:523: error: 'FLAC_PRIVATE' has no member named 'rbuffer'
flac.c:523: error: 'FLAC_PRIVATE' has no member named 'rbuffer'
flac.c:524: error: 'FLAC_PRIVATE' has no member named 'rbuffer'
flac.c: In function 'flac_enc_init':
flac.c:549: error: 'FLAC_PRIVATE' has no member named 'fse'
flac.c:549: warning: implicit declaration of function 'FLAC__seekable_stream_encoder_new'
flac.c:549: warning: nested extern declaration of 'FLAC__seekable_stream_encoder_new'
flac.c:551: warning: implicit declaration of function 'FLAC__seekable_stream_encoder_set_write_callback'
flac.c:551: warning: nested extern declaration of 'FLAC__seekable_stream_encoder_set_write_callback'
flac.c:551: error: 'FLAC_PRIVATE' has no member named 'fse'
flac.c:551: error: 'sf_flac_enc_write_callback' undeclared (first use in this function)
flac.c:551: error: (Each undeclared identifier is reported only once
flac.c:551: error: for each function it appears in.)
flac.c:552: warning: implicit declaration of function 'FLAC__seekable_stream_encoder_set_seek_callback'
flac.c:552: warning: nested extern declaration of 'FLAC__seekable_stream_encoder_set_seek_callback'
flac.c:552: error: 'FLAC_PRIVATE' has no member named 'fse'
flac.c:552: error: 'sf_flac_enc_seek_callback' undeclared (first use in this function)
flac.c:557: warning: implicit declaration of function 'FLAC__seekable_stream_encoder_set_client_data'
flac.c:557: warning: nested extern declaration of 'FLAC__seekable_stream_encoder_set_client_data'
flac.c:557: error: 'FLAC_PRIVATE' has no member named 'fse'
flac.c:558: warning: implicit declaration of function 'FLAC__seekable_stream_encoder_set_channels'
flac.c:558: warning: nested extern declaration of 'FLAC__seekable_stream_encoder_set_channels'
flac.c:558: error: 'FLAC_PRIVATE' has no member named 'fse'
flac.c:559: warning: implicit declaration of function 'FLAC__seekable_stream_encoder_set_sample_rate'
flac.c:559: warning: nested extern declaration of 'FLAC__seekable_stream_encoder_set_sample_rate'
flac.c:559: error: 'FLAC_PRIVATE' has no member named 'fse'
flac.c:577: warning: implicit declaration of function 'FLAC__seekable_stream_encoder_set_bits_per_sample'
flac.c:577: warning: nested extern declaration of 'FLAC__seekable_stream_encoder_set_bits_per_sample'
flac.c:577: error: 'FLAC_PRIVATE' has no member named 'fse'
flac.c:579: warning: implicit declaration of function 'FLAC__seekable_stream_encoder_init'
flac.c:579: warning: nested extern declaration of 'FLAC__seekable_stream_encoder_init'
flac.c:579: error: 'FLAC_PRIVATE' has no member named 'fse'
flac.c:579: error: 'FLAC__SEEKABLE_STREAM_DECODER_OK' undeclared (first use in this function)
flac.c:580: warning: implicit declaration of function 'FLAC__seekable_stream_encoder_get_resolved_state_string'
flac.c:580: warning: nested extern declaration of 'FLAC__seekable_stream_encoder_get_resolved_state_string'
flac.c:580: error: 'FLAC_PRIVATE' has no member named 'fse'
flac.c:586: error: 'FLAC_PRIVATE' has no member named 'encbuffer'
flac.c: In function 'flac_read_header':
flac.c:596: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:596: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_new'
flac.c:596: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_new'
flac.c:599: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_set_read_callback'
flac.c:599: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_set_read_callback'
flac.c:599: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:599: error: 'sf_flac_read_callback' undeclared (first use in this function)
flac.c:600: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_set_seek_callback'
flac.c:600: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_set_seek_callback'
flac.c:600: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:600: error: 'sf_flac_seek_callback' undeclared (first use in this function)
flac.c:601: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_set_tell_callback'
flac.c:601: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_set_tell_callback'
flac.c:601: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:601: error: 'sf_flac_tell_callback' undeclared (first use in this function)
flac.c:602: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_set_length_callback'
flac.c:602: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_set_length_callback'
flac.c:602: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:602: error: 'sf_flac_length_callback' undeclared (first use in this function)
flac.c:603: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_set_eof_callback'
flac.c:603: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_set_eof_callback'
flac.c:603: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:603: error: 'sf_flac_eof_callback' undeclared (first use in this function)
flac.c:604: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_set_write_callback'
flac.c:604: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_set_write_callback'
flac.c:604: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:604: error: 'sf_flac_write_callback' undeclared (first use in this function)
flac.c:605: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_set_metadata_callback'
flac.c:605: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_set_metadata_callback'
flac.c:605: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:605: error: 'sf_flac_meta_callback' undeclared (first use in this function)
flac.c:606: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_set_error_callback'
flac.c:606: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_set_error_callback'
flac.c:606: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:606: error: 'sf_flac_error_callback' undeclared (first use in this function)
flac.c:607: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_set_client_data'
flac.c:607: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_set_client_data'
flac.c:607: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:609: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_init'
flac.c:609: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_init'
flac.c:609: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:609: error: 'FLAC__SEEKABLE_STREAM_DECODER_OK' undeclared (first use in this function)
flac.c:612: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_process_until_end_of_metadata'
flac.c:612: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_process_until_end_of_metadata'
flac.c:612: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:615: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_get_decode_position'
flac.c:615: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_get_decode_position'
flac.c:615: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c: In function 'flac_read_loop':
flac.c:672: error: 'FLAC_PRIVATE' has no member named 'pos'
flac.c:673: error: 'FLAC_PRIVATE' has no member named 'len'
flac.c:674: error: 'FLAC_PRIVATE' has no member named 'remain'
flac.c:675: error: 'FLAC_PRIVATE' has no member named 'frame'
flac.c:675: error: 'FLAC_PRIVATE' has no member named 'bufferpos'
flac.c:675: error: 'FLAC_PRIVATE' has no member named 'frame'
flac.c:678: error: 'FLAC_PRIVATE' has no member named 'pos'
flac.c:678: error: 'FLAC_PRIVATE' has no member named 'len'
flac.c:679: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_process_single'
flac.c:679: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_process_single'
flac.c:679: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:681: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_get_state'
flac.c:681: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_get_state'
flac.c:681: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:681: error: 'FLAC__SEEKABLE_STREAM_DECODER_OK' undeclared (first use in this function)
flac.c:685: error: 'FLAC_PRIVATE' has no member named 'ptr'
flac.c:687: error: 'FLAC_PRIVATE' has no member named 'pos'
flac.c: In function 'flac_read_flac2s':
flac.c:696: error: 'FLAC_PRIVATE' has no member named 'pcmtype'
flac.c:699: error: 'FLAC_PRIVATE' has no member named 'ptr'
flac.c: In function 'flac_read_flac2i':
flac.c:716: error: 'FLAC_PRIVATE' has no member named 'pcmtype'
flac.c:719: error: 'FLAC_PRIVATE' has no member named 'ptr'
flac.c: In function 'flac_read_flac2f':
flac.c:736: error: 'FLAC_PRIVATE' has no member named 'pcmtype'
flac.c:739: error: 'FLAC_PRIVATE' has no member named 'ptr'
flac.c: In function 'flac_read_flac2d':
flac.c:756: error: 'FLAC_PRIVATE' has no member named 'pcmtype'
flac.c:759: error: 'FLAC_PRIVATE' has no member named 'ptr'
flac.c: In function 'flac_write_s2flac':
flac.c:776: error: 'FLAC_PRIVATE' has no member named 'encbuffer'
flac.c:798: warning: implicit declaration of function 'FLAC__seekable_stream_encoder_process_interleaved'
flac.c:798: warning: nested extern declaration of 'FLAC__seekable_stream_encoder_process_interleaved'
flac.c:798: error: 'FLAC_PRIVATE' has no member named 'fse'
flac.c: In function 'flac_write_i2flac':
flac.c:818: error: 'FLAC_PRIVATE' has no member named 'encbuffer'
flac.c:840: error: 'FLAC_PRIVATE' has no member named 'fse'
flac.c: In function 'flac_write_f2flac':
flac.c:860: error: 'FLAC_PRIVATE' has no member named 'encbuffer'
flac.c:882: error: 'FLAC_PRIVATE' has no member named 'fse'
flac.c: In function 'flac_write_d2flac':
flac.c:992: error: 'FLAC_PRIVATE' has no member named 'encbuffer'
flac.c:1014: error: 'FLAC_PRIVATE' has no member named 'fse'
flac.c: In function 'flac_seek':
flac.c:1130: error: 'FLAC_PRIVATE' has no member named 'frame'
flac.c:1134: warning: implicit declaration of function 'FLAC__seekable_stream_decoder_seek_absolute'
flac.c:1134: warning: nested extern declaration of 'FLAC__seekable_stream_decoder_seek_absolute'
flac.c:1134: error: 'FLAC_PRIVATE' has no member named 'fsd'
flac.c:1135: error: 'FLAC_PRIVATE' has no member named 'fsd'
make[3]: *** [flac.lo] Error 1
make[3]: Leaving directory `/home/bldyman/libsndfile-1.0.17/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/bldyman/libsndfile-1.0.17/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/bldyman/libsndfile-1.0.17/src'
make: *** [all-recursive] Error 1

```

How can I do?
thanxx in advance

---

### Post by Yellow Pasque on 2008-10-12
Are you on an older version of Ubuntu (older than Hardy/8.04)? If not, sooperlooper and libsndfile are available in the repository.

---

### Post by bldyman on 2008-10-12
oh you are right!
I was compiling other packages and I did'n check for this one! I'm sorry. thank you!

---

