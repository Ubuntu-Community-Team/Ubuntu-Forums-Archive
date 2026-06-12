---
title: "JfBUILD and jfDuke will not install"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by Necrom@ncer on 2009-04-04
Jonof's site has no straightforward guide for linux users, so I extract both JFBuild and Duke to the same directory, merge everything, and type "make" in the console, but I get "src/sound.c:5:18: error: fmod.h: No such file or directory
src/sound.c:6:25: error: fmod_errors.h: No such file or directory
src/sound.c:29: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/sound.c:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘f_open’
src/sound.c:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘f_close’
src/sound.c:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘f_read’
src/sound.c:53: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘f_seek’
src/sound.c:58: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘f_tell’
src/sound.c: In function ‘initsb’:
src/sound.c:78: error: ‘FMOD_VERSION’ undeclared (first use in this function)
src/sound.c:78: error: (Each undeclared identifier is reported only once
src/sound.c:78: error: for each function it appears in.)
src/sound.c:79: warning: implicit declaration of function ‘FSOUND_GetVersion’
src/sound.c:90: warning: implicit declaration of function ‘FSOUND_Init’
src/sound.c:94: warning: implicit declaration of function ‘FMOD_ErrorString’
src/sound.c:94: warning: implicit declaration of function ‘FSOUND_GetError’
src/sound.c:97: warning: implicit declaration of function ‘FSOUND_GetOutput’
src/sound.c:98: error: ‘FSOUND_OUTPUT_NOSOUND’ undeclared (first use in this function)
src/sound.c:99: error: ‘FSOUND_OUTPUT_WINMM’ undeclared (first use in this function)
src/sound.c:100: error: ‘FSOUND_OUTPUT_DSOUND’ undeclared (first use in this function)
src/sound.c:101: error: ‘FSOUND_OUTPUT_OSS’ undeclared (first use in this function)
src/sound.c:102: error: ‘FSOUND_OUTPUT_ESD’ undeclared (first use in this function)
src/sound.c:103: error: ‘FSOUND_OUTPUT_ALSA’ undeclared (first use in this function)
src/sound.c:104: error: ‘FSOUND_OUTPUT_ASIO’ undeclared (first use in this function)
src/sound.c:109: warning: implicit declaration of function ‘FSOUND_File_SetCallbacks’
src/sound.c:110: error: ‘FSOUND_OPENCALLBACK’ undeclared (first use in this function)
src/sound.c:110: error: expected ‘)’ before ‘f_open’
src/sound.c: In function ‘uninitsb’:
src/sound.c:125: warning: implicit declaration of function ‘FSOUND_Close’
src/sound.c: In function ‘wsayfollow’:
src/sound.c:179: warning: implicit declaration of function ‘FSOUND_IsPlaying’
src/sound.c:185: warning: implicit declaration of function ‘FSOUND_GetCurrentPosition’
src/sound.c:185: warning: comparison between signed and unsigned
src/sound.c:192: warning: implicit declaration of function ‘FSOUND_StopSound’
src/sound.c:196: warning: implicit declaration of function ‘FSOUND_PlaySoundEx’
src/sound.c:196: error: ‘FSOUND_FREE’ undeclared (first use in this function)
src/sound.c:196: error: ‘samples’ undeclared (first use in this function)
src/sound.c:198: warning: implicit declaration of function ‘FSOUND_SetFrequency’
src/sound.c:199: warning: implicit declaration of function ‘FSOUND_SetVolume’
src/sound.c:201: warning: implicit declaration of function ‘FSOUND_SetPaused’
src/sound.c: In function ‘wsay’:
src/sound.c:240: warning: comparison between signed and unsigned
src/sound.c:251: error: ‘FSOUND_FREE’ undeclared (first use in this function)
src/sound.c:251: error: ‘samples’ undeclared (first use in this function)
src/sound.c: In function ‘loadwaves’:
src/sound.c:299: error: ‘samples’ undeclared (first use in this function)
src/sound.c:305: error: ‘FSOUND_LOOP_NORMAL’ undeclared (first use in this function)
src/sound.c:306: error: ‘FSOUND_LOOP_OFF’ undeclared (first use in this function)
src/sound.c:307: warning: implicit declaration of function ‘FSOUND_Sample_Alloc’
src/sound.c:307: error: ‘FSOUND_FREE’ undeclared (first use in this function)
src/sound.c:312: warning: implicit declaration of function ‘FSOUND_Sample_Upload’
src/sound.c:312: error: ‘FSOUND_8BITS’ undeclared (first use in this function)
src/sound.c:312: error: ‘FSOUND_MONO’ undeclared (first use in this function)
src/sound.c:312: error: ‘FSOUND_UNSIGNED’ undeclared (first use in this function)
src/sound.c:315: warning: implicit declaration of function ‘FSOUND_Sample_SetLoopPoints’
src/sound.c: At top level:
src/sound.c:325: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/sound.c: In function ‘loadsong’:
src/sound.c:331: error: ‘musicstream’ undeclared (first use in this function)
src/sound.c:333: warning: implicit declaration of function ‘FSOUND_Stream_OpenFile’
src/sound.c:333: error: ‘FSOUND_LOOP_NORMAL’ undeclared (first use in this function)
src/sound.c: In function ‘musicon’:
src/sound.c:342: error: ‘musicstream’ undeclared (first use in this function)
src/sound.c:343: warning: implicit declaration of function ‘FSOUND_Stream_Play’
src/sound.c:343: error: ‘FSOUND_FREE’ undeclared (first use in this function)
src/sound.c: In function ‘musicoff’:
src/sound.c:350: error: ‘musicstream’ undeclared (first use in this function)
src/sound.c:351: warning: implicit declaration of function ‘FSOUND_Stream_Stop’
make: *** [obj.gnu/sound.o] Error 1"

What am i doing wrong?

---

### Post by cariboo on 2009-04-04
Could you provide a link to the howto?

Jim

---

### Post by Necrom@ncer on 2009-04-04
Jonof has no guide, just what you need... [http://www.jonof.id.au/index.php?p=jfbuild](http://www.jonof.id.au/index.php?p=jfbuild) has that.

---

