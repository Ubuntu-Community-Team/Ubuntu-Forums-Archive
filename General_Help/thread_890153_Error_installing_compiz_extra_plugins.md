---
title: "Error installing compiz extra plugins"
date: 2008-08-14
forum: General Help
---

### Post by ranjithnair on 2008-08-14
Error while installing the extra plugins for ubuntu. I put the follwing command for installing the plugins required to compile the plugins

sudo apt-get install compiz-bcop compiz-dev compizconfig-settings-manager build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core

After downloading the plugin atlantis2 when i tried to install it i got..

ranjith@ubuntu:~$ cd ~/compiz/atlantis2
ranjith@ubuntu:~/compiz/atlantis2$ sudo make
[sudo] password for ranjith: 
compiling : build/atlantis_options.c -> build/atlantis_options.loIn file included from build/atlantis_options.c:19:
build/atlantis_options.h:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.h:93: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetStartCrabsBottom&#8217;
build/atlantis_options.h:97: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetSchoolSimilarGroups&#8217;
build/atlantis_options.h:101: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetLowPoly&#8217;
build/atlantis_options.h:105: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.h:110: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.h:114: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.h:118: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.h:122: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.h:127: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.h:131: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.h:135: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.h:139: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetShowWater&#8217;
build/atlantis_options.h:143: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetShowWaterWire&#8217;
build/atlantis_options.h:147: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetShowGround&#8217;
build/atlantis_options.h:175: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetRenderWaves&#8217;
build/atlantis_options.h:179: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetWaveRipple&#8217;
build/atlantis_options.h:199: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetRescaleWidth&#8217;
build/atlantis_options.h:203: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetRotateLighting&#8217;
build/atlantis_options.c:25: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_optons.c:26: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisOptionsVTable&#8217;
build/atlantis_options.c:48: error: array type has incomplete element type
build/atlantis_options.c: In function &#8216;atlantisGetSpeedFactor&#8217;:
build/atlantis_options.c:56: error: dereferencing pointer to incomplete type
build/atlantis_options.c:56: error: dereferencing pointer to incomplete type
build/atlantis_options.c:58: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetSpeedFactorOption&#8217;:
build/atlantis_options.c:62: error: dereferencing pointer to incomplete type
build/atlantis_options.c:62: error: dereferencing pointer to incomplete type
build/atlantis_options.c:64: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetSpeedFactorNotify&#8217;:
build/atlantis_options.c:68: error: dereferencing pointer to incomplete type
build/atlantis_options.c:68: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:72: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetStartCrabsBottom&#8217;
build/atlantis_options.c: In function &#8216;atlantisGetStartCrabsBottomOption&#8217;:
build/atlantis_options.c:80: error: dereferencing pointer to incomplete type
build/atlantis_options.c:80: error: dereferencing pointer to incomplete type
build/atlantis_options.c:82: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetStartCrabsBottomNotify&#8217;:
build/atlantis_options.c:86: error: dereferencing pointer to incomplete type
build/atlantis_options.c:86: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:90: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetSchoolSimilarGroups&#8217;
build/atlantis_options.c: In function &#8216;atlantisGetSchoolSimilarGroupsOption&#8217;:
build/atlantis_options.c:98: error: dereferencing pointer to incomplete type
build/atlantis_options.c:98: error: dereferencing pointer to incomplete type
build/atlantis_options.c:100: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetSchoolSimilarGroupsNotify&#8217;:
build/atlantis_options.c:104: error: dereferencing pointer to incomplete type
build/atlantis_options.c:104: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:108: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetLowPoly&#8217;
build/atlantis_options.c: In function &#8216;atlantisGetLowPolyOption&#8217;:
build/atlantis_options.c:116: error: dereferencing pointer to incomplete type
build/atlantis_options.c:116: error: dereferencing pointer to incomplete type
build/atlantis_options.c:118: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetLowPolyNotify&#8217;:
build/atlantis_options.c:122: error: dereferencing pointer to incomplete type
build/atlantis_options.c:122: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:126: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.c: In function &#8216;atlantisGetCreatureTypeMask&#8217;:
build/atlantis_options.c:134: error: dereferencing pointer to incomplete type
build/atlantis_options.c:134: error: dereferencing pointer to incomplete type
build/atlantis_options.c: In function &#8216;atlantisGetCreatureTypeOption&#8217;:
build/atlantis_options.c:140: error: dereferencing pointer to incomplete type
build/atlantis_options.c:140: error: dereferencing pointer to incomplete type
build/atlantis_options.c:142: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetCreatureTypeNotify&#8217;:
build/atlantis_options.c:146: error: dereferencing pointer to incomplete type
build/atlantis_options.c:146: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:150: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.c: In function &#8216;atlantisGetCreatureColorOption&#8217;:
build/atlantis_options.c:158: error: dereferencing pointer to incomplete type
build/atlantis_options.c:158: error: dereferencing pointer to incomplete type
build/atlantis_options.c:160: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetCreatureColorNotify&#8217;:
build/atlantis_options.c:164: error: dereferencing pointer to incomplete type
build/atlantis_options.c:164: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:168: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.c: In function &#8216;atlantisGetCreatureNumberOption&#8217;:
build/atlantis_options.c:176: error: dereferencing pointer to incomplete type
build/atlantis_options.c:176: error: dereferencing pointer to incomplete type
build/atlantis_options.c:178: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetCreatureNumberNotify&#8217;:
build/atlantis_options.c:182: error: dereferencing pointer to incomplete type
build/atlantis_options.c:182: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:186: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.c: In function &#8216;atlantisGetCreatureSizeOption&#8217;:
build/atlantis_options.c:194: error: dereferencing pointer to incomplete type
build/atlantis_options.c:194: error: dereferencing pointer to incomplete type
build/atlantis_options.c:196: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetCreatureSizeNotify&#8217;:
build/atlantis_options.c:200: error: dereferencing pointer to incomplete type
build/atlantis_options.c:200: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:204: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.c: In function &#8216;atlantisGetPlantTypeMask&#8217;:
build/atlantis_options.c:212: error: dereferencing pointer to incomplete type
build/atlantis_options.c:212: error: dereferencing pointer to incomplete type
build/atlantis_options.c: In function &#8216;atlantisGetPlantTypeOption&#8217;:
build/atlantis_options.c:218: error: dereferencing pointer to incomplete type
build/atlantis_options.c:218: error: dereferencing pointer to incomplete type
build/atlantis_options.c:220: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetPlantTypeNotify&#8217;:
build/atlantis_options.c:224: error: dereferencing pointer to incomplete type
build/atlantis_options.c:224: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:228: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.c: In function &#8216;atlantisGetPlantColorOption&#8217;:
build/atlantis_options.c:236: error: dereferencing pointer to incomplete type
build/atlantis_options.c:236: error: dereferencing pointer to incomplete type
build/atlantis_options.c:238: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetPlantColorNotify&#8217;:
build/atlantis_options.c:242: error: dereferencing pointer to incomplete type
build/atlantis_options.c:242: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:246: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.c: In function &#8216;atlantisGetPlantNumberOption&#8217;:
build/atlantis_options.c:254: error: dereferencing pointer to incomplete type
build/atlantis_options.c:254: error: dereferencing pointer to incomplete type
build/atlantis_options.c:256: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetPlantNumberNotify&#8217;:
build/atlantis_options.c:260: error: dereferencing pointer to incomplete type
build/atlantis_options.c:260: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:264: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
build/atlantis_options.c: In function &#8216;atlantisGetPlantSizeOption&#8217;:
build/atlantis_options.c:272: error: dereferencing pointer to incomplete type
build/atlantis_options.c:272: error: dereferencing pointer to incomplete type
build/atlantis_options.c:274: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetPlantSizeNotify&#8217;:
build/atlantis_options.c:278: error: dereferencing pointer to incomplete type
build/atlantis_options.c:278: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:282: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetShowWater&#8217;
build/atlantis_options.c: In function &#8216;atlantisGetShowWaterOption&#8217;:
build/atlantis_options.c:290: error: dereferencing pointer to incomplete type
build/atlantis_options.c:290: error: dereferencing pointer to incomplete type
build/atlantis_options.c:292: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetShowWaterNotify&#8217;:
build/atlantis_options.c:296: error: dereferencing pointer to incomplete type
build/atlantis_options.c:296: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:300: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetShowWaterWire&#8217;
build/atlantis_options.c: In function &#8216;atlantisGetShowWaterWireOption&#8217;:
build/atlantis_options.c:308: error: dereferencing pointer to incomplete type
build/atlantis_options.c:308: error: dereferencing pointer to incomplete type
build/atlantis_options.c:310: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetShowWaterWireNotify&#8217;:
build/atlantis_options.c:314: error: dereferencing pointer to incomplete type
build/atlantis_options.c:314: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:318: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetShowGround&#8217;
build/atlantis_options.c: In function &#8216;atlantisGetShowGroundOption&#8217;:
build/atlantis_options.c:326: error: dereferencing pointer to incomplete type
build/atlantis_options.c:326: error: dereferencing pointer to incomplete type
build/atlantis_options.c:328: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetShowGroundNotify&#8217;:
build/atlantis_options.c:332: error: dereferencing pointer to incomplete type
build/atlantis_options.c:332: error: dereferencing pointer to incomplete type
build/atlantis_options.c: In function &#8216;atlantisGetGroundColor&#8217;:
build/atlantis_options.c:338: error: dereferencing pointer to incomplete type
build/atlantis_options.c:338: error: dereferencing pointer to incomplete type
build/atlantis_options.c:340: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetGroundColorRed&#8217;:
build/atlantis_options.c:344: error: dereferencing pointer to incomplete type
build/atlantis_options.c:344: error: dereferencing pointer to incomplete type
build/atlantis_options.c:346: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetGroundColorGreen&#8217;:
build/atlantis_options.c:350: error: dereferencing pointer to incomplete type
build/atlantis_options.c:350: error: dereferencing pointer to incomplete type
build/atlantis_options.c:352: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetGroundColorBlue&#8217;:
build/atlantis_options.c:356: error: dereferencing pointer to incomplete type
build/atlantis_options.c:356: error: dereferencing pointer to incomplete type
build/atlantis_options.c:358: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetGroundColorAlpha&#8217;:
build/atlantis_options.c:362: error: dereferencing pointer to incomplete type
build/atlantis_options.c:362: error: dereferencing pointer to incomplete type
build/atlantis_options.c:364: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetGroundColorOption&#8217;:
build/atlantis_options.c:368: error: dereferencing pointer to incomplete type
build/atlantis_options.c:368: error: dereferencing pointer to incomplete type
build/atlantis_options.c:370: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetGroundColorNotify&#8217;:
build/atlantis_options.c:374: error: dereferencing pointer to incomplete type
build/atlantis_options.c:374: error: dereferencing pointer to incomplete type
build/atlantis_options.c: In function &#8216;atlantisGetWaterHeight&#8217;:
build/atlantis_options.c:380: error: dereferencing pointer to incomplete type
build/atlantis_options.c:380: error: dereferencing pointer to incomplete type
build/atlantis_options.c:382: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetWaterHeightOption&#8217;:
build/atlantis_options.c:386: error: dereferencing pointer to incomplete type
build/atlantis_options.c:386: error: dereferencing pointer to incomplete type
build/atlantis_options.c:388: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetWaterHeightNotify&#8217;:
build/atlantis_options.c:392: error: dereferencing pointer to incomplete type
build/atlantis_options.c:392: error: dereferencing pointer to incomplete type
build/atlantis_options.c: In function &#8216;atlantisGetWaterColor&#8217;:
build/atlantis_options.c:398: error: dereferencing pointer to incomplete type
build/atlantis_options.c:398: error: dereferencing pointer to incomplete type
build/atlantis_options.c:400: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetWaterColorRed&#8217;:
build/atlantis_options.c:404: error: dereferencing pointer to incomplete type
build/atlantis_options.c:404: error: dereferencing pointer to incomplete type
build/atlantis_options.c:406: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetWaterColorGreen&#8217;:
build/atlantis_options.c:410: error: dereferencing pointer to incomplete type
build/atlantis_options.c:410: error: dereferencing pointer to incomplete type
build/atlantis_options.c:412: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetWaterColorBlue&#8217;:
build/atlantis_options.c:416: error: dereferencing pointer to incomplete type
build/atlantis_options.c:416: error: dereferencing pointer to incomplete type
build/atlantis_options.c:418: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetWaterColorAlpha&#8217;:
build/atlantis_options.c:422: error: dereferencing pointer to incomplete type
build/atlantis_options.c:422: error: dereferencing pointer to incomplete type
build/atlantis_options.c:424: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetWaterColorOption&#8217;:
build/atlantis_options.c:428: error: dereferencing pointer to incomplete type
build/atlantis_options.c:428: error: dereferencing pointer to incomplete type
build/atlantis_options.c:430: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetWaterColorNotify&#8217;:
build/atlantis_options.c:434: error: dereferencing pointer to incomplete type
build/atlantis_options.c:434: error: dereferencing pointer to incomplete type
build/atlantis_options.c: In function &#8216;atlantisGetGridQuality&#8217;:
build/atlantis_options.c:440: error: dereferencing pointer to incomplete type
build/atlantis_options.c:440: error: dereferencing pointer to incomplete type
build/atlantis_options.c:442: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetGridQualityOption&#8217;:
build/atlantis_options.c:446: error: dereferencing pointer to incomplete type
build/atlantis_options.c:446: error: dereferencing pointer to incomplete type
build/atlantis_options.c:448: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetGridQualityNotify&#8217;:
build/atlantis_options.c:452: error: dereferencing pointer to incomplete type
build/atlantis_options.c:452: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:456: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetRenderWaves&#8217;
build/atlantis_options.c: In function &#8216;atlantisGetRenderWavesOption&#8217;:
build/atlantis_options.c:464: error: dereferencing pointer to incomplete type
build/atlantis_options.c:464: error: dereferencing pointer to incomplete type
build/atlantis_options.c:466: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetRenderWavesNotify&#8217;:
build/atlantis_options.c:470: error: dereferencing pointer to incomplete type
build/atlantis_options.c:470: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:474: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetWaveRipple&#8217;
build/atlantis_options.c: In function &#8216;atlantisGetWaveRippleOption&#8217;:
build/atlantis_options.c:482: error: dereferencing pointer to incomplete type
build/atlantis_options.c:482: error: dereferencing pointer to incomplete type
build/atlantis_options.c:484: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetWaveRippleNotify&#8217;:
build/atlantis_options.c:488: error: dereferencing pointer to incomplete type
build/atlantis_options.c:488: error: dereferencing pointer to incomplete type
build/atlantis_options.c: In function &#8216;atlantisGetWaveAmplitude&#8217;:
build/atlantis_options.c:494: error: dereferencing pointer to incomplete type
build/atlantis_options.c:494: error: dereferencing pointer to incomplete type
build/atlantis_options.c:496: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetWaveAmplitudeOption&#8217;:
build/atlantis_options.c:500: error: dereferencing pointer to incomplete type
build/atlantis_options.c:500: error: dereferencing pointer to incomplete type
build/atlantis_options.c:502: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetWaveAmplitudeNotify&#8217;:
build/atlantis_options.c:506: error: dereferencing pointer to incomplete type
build/atlantis_options.c:506: error: dereferencing pointer to incomplete type
build/atlantis_options.c: In function &#8216;atlantisGetWaveFrequency&#8217;:
build/atlantis_options.c:512: error: dereferencing pointer to incomplete type
build/atlantis_options.c:512: error: dereferencing pointer to incomplete type
build/atlantis_options.c:514: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetWaveFrequencyOption&#8217;:
build/atlantis_options.c:518: error: dereferencing pointer to incomplete type
build/atlantis_options.c:518: error: dereferencing pointer to incomplete type
build/atlantis_options.c:520: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetWaveFrequencyNotify&#8217;:
build/atlantis_options.c:524: error: dereferencing pointer to incomplete type
build/atlantis_options.c:524: error: dereferencing pointer to incomplete type
build/atlantis_options.c: In function &#8216;atlantisGetSmallWaveAmplitude&#8217;:
build/atlantis_options.c:530: error: dereferencing pointer to incomplete type
build/atlantis_options.c:530: error: dereferencing pointer to incomplete type
build/atlantis_options.c:532: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetSmallWaveAmplitudeOption&#8217;:
build/atlantis_options.c:536: error: dereferencing pointer to incomplete type
build/atlantis_options.c:536: error: dereferencing pointer to incomplete type
build/atlantis_options.c:538: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetSmallWaveAmplitudeNotify&#8217;:
build/atlantis_options.c:542: error: dereferencing pointer to incomplete type
build/atlantis_options.c:542: error: dereferencing pointer to incomplete type
build/atlantis_options.c: In function &#8216;atlantisGetSmallWaveFrequency&#8217;:
build/atlantis_options.c:548: error: dereferencing pointer to incomplete type
build/atlantis_options.c:548: error: dereferencing pointer to incomplete type
build/atlantis_options.c:550: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetSmallWaveFrequencyOption&#8217;:
build/atlantis_options.c:554: error: dereferencing pointer to incomplete type
build/atlantis_options.c:554: error: dereferencing pointer to incomplete type
build/atlantis_options.c:556: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetSmallWaveFrequencyNotify&#8217;:
build/atlantis_options.c:560: error: dereferencing pointer to incomplete type
build/atlantis_options.c:560: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:564: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetRescaleWidth&#8217;
build/atlantis_options.c: In function &#8216;atlantisGetRescaleWidthOption&#8217;:
build/atlantis_options.c:572: error: dereferencing pointer to incomplete type
build/atlantis_options.c:572: error: dereferencing pointer to incomplete type
build/atlantis_options.c:574: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetRescaleWidthNotify&#8217;:
build/atlantis_options.c:578: error: dereferencing pointer to incomplete type
build/atlantis_options.c:578: error: dereferencing pointer to incomplete type
build/atlantis_options.c: At top level:
build/atlantis_options.c:582: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisGetRotateLighting&#8217;
build/atlantis_options.c: In function &#8216;atlantisGetRotateLightingOption&#8217;:
build/atlantis_options.c:590: error: dereferencing pointer to incomplete type
build/atlantis_options.c:590: error: dereferencing pointer to incomplete type
build/atlantis_options.c:592: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetRotateLightingNotify&#8217;:
build/atlantis_options.c:596: error: dereferencing pointer to incomplete type
build/atlantis_options.c:596: error: dereferencing pointer to incomplete type
build/atlantis_options.c: In function &#8216;atlantisGetLightInclination&#8217;:
build/atlantis_options.c:602: error: dereferencing pointer to incomplete type
build/atlantis_options.c:602: error: dereferencing pointer to incomplete type
build/atlantis_options.c:604: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetLightInclinationOption&#8217;:
build/atlantis_options.c:608: error: dereferencing pointer to incomplete type
build/atlantis_options.c:608: error: dereferencing pointer to incomplete type
build/atlantis_options.c:610: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetLightInclinationNotify&#8217;:
build/atlantis_options.c:614: error: dereferencing pointer to incomplete type
build/atlantis_options.c:614: error: dereferencing pointer to incomplete type
build/atlantis_options.c: In function &#8216;atlantisGetLightAmbient&#8217;:
build/atlantis_options.c:620: error: dereferencing pointer to incomplete type
build/atlantis_options.c:620: error: dereferencing pointer to incomplete type
build/atlantis_options.c:622: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisGetLightAmbientOption&#8217;:
build/atlantis_options.c:626: error: dereferencing pointer to incomplete type
build/atlantis_options.c:626: error: dereferencing pointer to incomplete type
build/atlantis_options.c:628: warning: control reaches end of non-void function
build/atlantis_options.c: In function &#8216;atlantisSetLightAmbientNotify&#8217;:
build/atlantis_options.c:632: error: dereferencing pointer to incomplete type
build/atlantis_options.c:632: error: dereferencing pointer to incomplete type
build/atlantis_options.c: In function &#8216;atlantisGetScreenOption&#8217;:
build/atlantis_options.c:638: error: dereferencing pointer to incomplete type
build/atlantis_options.c:638: error: dereferencing pointer to incomplete type
build/atlantis_options.c:640: warning: control reaches end of non-void function
build/atlantis_options.c: At top level:
build/atlantis_options.c:642: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisOptionsScreenOptionInfo&#8217;
build/atlantis_options.c:674: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisOptionsSetScreenOption&#8217;
build/atlantis_options.c: In function &#8216;atlantisOptionsGetScreenOptions&#8217;:
build/atlantis_options.c:935: error: dereferencing pointer to incomplete type
build/atlantis_options.c:935: error: dereferencing pointer to incomplete type
build/atlantis_options.c:938: warning: control reaches end of non-void function
build/atlantis_options.c: At top level:
build/atlantis_options.c:940: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisOptionsInitScreen&#8217;
build/atlantis_options.c: In function &#8216;atlantisOptionsFiniScreen&#8217;:
build/atlantis_options.c:976: error: &#8216;atlantisPluginVTable&#8217; undeclared (first use in this function)
build/atlantis_options.c:976: error: (Each undeclared identifier is reported only once
build/atlantis_options.c:976: error: for each function it appears in.)
build/atlantis_options.c:977: warning: &#8216;return&#8217; with a value, in function returning void
build/atlantis_options.c:979: error: dereferencing pointer to incomplete type
build/atlantis_options.c:979: error: dereferencing pointer to incomplete type
build/atlantis_options.c:982: warning: implicit declaration of function &#8216;compFiniScreenOptions&#8217;
build/atlantis_options.c:982: warning: nested extern declaration of &#8216;compFiniScreenOptions&#8217;
build/atlantis_options.c: At top level:
build/atlantis_options.c:987: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisOptionsInitDisplay&#8217;
build/atlantis_options.c: In function &#8216;atlantisOptionsFiniDisplay&#8217;:
build/atlantis_options.c:1012: error: &#8216;atlantisPluginVTable&#8217; undeclared (first use in this function)
build/atlantis_options.c:1013: warning: &#8216;return&#8217; with a value, in function returning void
build/atlantis_options.c:1015: error: dereferencing pointer to incomplete type
build/atlantis_options.c:1017: warning: implicit declaration of function &#8216;freeScreenPrivateIndex&#8217;
build/atlantis_options.c:1017: warning: nested extern declaration of &#8216;freeScreenPrivateIndex&#8217;
build/atlantis_options.c: At top level:
build/atlantis_options.c:1021: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;atlantisOptionsInit&#8217;
build/atlantis_options.c: In function &#8216;atlantisOptionsFini&#8217;:
build/atlantis_options.c:1038: error: &#8216;atlantisPluginVTable&#8217; undeclared (first use in this function)
build/atlantis_options.c:1039: warning: &#8216;return&#8217; with a value, in function returning void
build/atlantis_options.c:1042: warning: implicit declaration of function &#8216;freeDisplayPrivateIndex&#8217;
build/atlantis_options.c:1042: warning: nested extern declaration of &#8216;freeDisplayPrivateIndex&#8217;
build/atlantis_options.c: At top level:
build/atlantis_options.c:1053: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
make: *** [build/atlantis_options.lo] Error 1

---

### Post by ZarathustraDK on 2008-08-14
Hmm...not really sure, try get this version:

```
git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2
```

See if it makes any difference when compiling it. The files should land in ~/atlantis2/

---

