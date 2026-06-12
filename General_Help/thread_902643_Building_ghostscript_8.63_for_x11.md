---
title: "Building ghostscript 8.63 for x11"
date: 2008-08-27
forum: General Help
---

### Post by horrendo on 2008-08-27
I'm trying to build the latest ghostscript on Ubuntu 8.04.  Here's the configure line I'm using ...

./configure --prefix={some directory} --disable-cups --with-x

This doesn't show any errors.  Here is an excerpt from the configure output ...

:
checking for GTK+ 2.x... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for cairo... yes
checking for X... libraries , headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for XOpenDisplay in -lX11... yes
checking for XdbeQueryExtension in -lXext... yes
checking for XtAppCreateShell in -lXt... no
:

Here's the output from gs --help from the resulting binary ...

stbaldwin@au-stb-mobile:~/dev/temp_bin/bin$ ./gs --help
GPL Ghostscript 8.63 (2008-08-01)
Copyright (C) 2008 Artifex Software, Inc.  All rights reserved.
Usage: gs [switches] [file1.ps file2.ps ...]
Most frequently used switches: (you can use # in place of =)
 -dNOPAUSE           no pause after page   | -q       `quiet', fewer messages
 -g<width>x<height>  page size in pixels   | -r<res>  pixels/inch resolution
 -sDEVICE=<devname>  select device         | -dBATCH  exit after last file
 -sOutputFile=<file> select output file: - for stdout, |command for pipe,
                                         embed %d or %ld for page #
Input formats: PostScript PostScriptLevel1 PostScriptLevel2 PostScriptLevel3 PDF
Default output device: bbox
Available devices:
   alc1900 alc2000 alc4000 alc4100 alc8500 alc8600 alc9100 ap3250 appledmp
   atx23 atx24 atx38 bbox bit bitcmyk bitrgb bitrgbtags bj10e bj10v bj10vh
   bj200 bjc600 bjc800 bjc880j bjccmyk bjccolor bjcgray bjcmono bmp16 bmp16m
   bmp256 bmp32b bmpgray bmpmono bmpsep1 bmpsep8 cairo ccr cdeskjet cdj1600
   cdj500 cdj550 cdj670 cdj850 cdj880 cdj890 cdj970 cdjcolor cdjmono cfax
   cgm24 cgm8 cgmmono chp2200 cif cljet5 cljet5c cljet5pr coslw2p coslwxl
   cp50 declj250 deskjet devicen dfaxhigh dfaxlow dj505j djet500 djet500c
   dl2100 dnj650c epl2050 epl2050p epl2120 epl2500 epl2750 epl5800 epl5900
   epl6100 epl6200 eps9high eps9mid epson epsonc epswrite escp escpage faxg3
   faxg32d faxg4 fmlbp fmpr fs600 gdi hl1240 hl1250 hl7x0 hpdj1120c hpdj310
   hpdj320 hpdj340 hpdj400 hpdj500 hpdj500c hpdj510 hpdj520 hpdj540 hpdj550c
   hpdj560c hpdj600 hpdj660c hpdj670c hpdj680c hpdj690c hpdj850c hpdj855c
   hpdj870c hpdj890c hpdjplus hpdjportable ibmpro ijs imagen imdi inferno
   iwhi iwlo iwlq jetp3852 jj100 jpeg jpegcmyk jpeggray la50 la70 la75
   la75plus laserjet lbp310 lbp320 lbp8 lex2050 lex3200 lex5700 lex7000
   lips2p lips3 lips4 lips4v lj250 lj3100sw lj4dith lj4dithp lj5gray lj5mono
   ljet2p ljet3 ljet3d ljet4 ljet4d ljet4pjl ljetplus ln03 lp1800 lp1900
   lp2000 lp2200 lp2400 lp2500 lp2563 lp3000c lp7500 lp7700 lp7900 lp8000
   lp8000c lp8100 lp8200c lp8300c lp8300f lp8400f lp8500c lp8600 lp8600f
   lp8700 lp8800c lp8900 lp9000b lp9000c lp9100 lp9200b lp9200c lp9300
   lp9400 lp9500c lp9600 lp9600s lp9800c lps4500 lps6500 lq850 lx5000
   lxm3200 lxm5700m m8510 mag16 mag256 md1xMono md2k md50Eco md50Mono md5k
   mgr4 mgr8 mgrgray2 mgrgray4 mgrgray8 mgrmono miff24 mj500c mj6000c
   mj700v2c mj8000c ml600 necp6 npdl nullpage oce9050 oki182 oki4w okiibm
   omni oprp opvp paintjet pam pbm pbmraw pcl3 pcx16 pcx24b pcx256 pcx2up
   pcxcmyk pcxgray pcxmono pdfwrite pgm pgmraw pgnm pgnmraw photoex picty180
   pj pjetxl pjxl pjxl300 pkm pkmraw pksm pksmraw plan9bm png16 png16m
   png256 png48 pngalpha pnggray pngmono pnm pnmraw ppm ppmraw pr1000
   pr1000_4 pr150 pr201 ps2write psdcmyk psdrgb psgray psmono psrgb pswrite
   pxlcolor pxlmono r4081 rinkj rpdl samsunggdi sgirgb sj48 spotcmyk st800
   stcolor sunhmono svg t4693d2 t4693d4 t4693d8 tek4696 tiff12nc tiff24nc
   tiff32nc tiffcrle tiffg3 tiffg32d tiffg4 tiffgray tifflzw tiffpack
   tiffsep uniprint wtscmyk wtsimdi xcf xes
Search path:
   . : %rom%lib/ :
:

Whereas the version of ghostscript that is bundled with Ubuntu 8.04
looks like this ...

stbaldwin@au-stb-mobile:~/dev/temp_bin/bin$ gs --help
GPL Ghostscript 8.61 (2007-11-21)
Copyright (C) 2007 Artifex Software, Inc.  All rights reserved.
Usage: gs [switches] [file1.ps file2.ps ...]
Most frequently used switches: (you can use # in place of =)
 -dNOPAUSE           no pause after page   | -q       `quiet', fewer messages
 -g<width>x<height>  page size in pixels   | -r<res>  pixels/inch resolution
 -sDEVICE=<devname>  select device         | -dBATCH  exit after last file
 -sOutputFile=<file> select output file: - for stdout, |command for pipe,
                                         embed %d or %ld for page #
Input formats: PostScript PostScriptLevel1 PostScriptLevel2 PostScriptLevel3 PDF
Default output device: x11alpha
Available devices:
   alc1900 alc2000 alc4000 alc4100 alc8500 alc8600 alc9100 ap3250 appledmp
   atx23 atx24 atx38 bbox bit bitcmyk bitrgb bitrgbtags bj10e bj10v bj10vh
   bj200 bjc600 bjc800 bjc880j bjccmyk bjccolor bjcgray bjcmono bmp16 bmp16m
   bmp256 bmp32b bmpgray bmpmono bmpsep1 bmpsep8 ccr cdeskjet cdj1600 cdj500
   cdj550 cdj670 cdj850 cdj880 cdj890 cdj970 cdjcolor cdjmono cfax cgm24
   cgm8 cgmmono chp2200 cif cljet5 cljet5c cljet5pr coslw2p coslwxl cp50
   cups declj250 deskjet devicen dfaxhigh dfaxlow display dj505j djet500
   djet500c dl2100 dnj650c epl2050 epl2050p epl2120 epl2500 epl2750 epl5800
   epl5900 epl6100 epl6200 eps9high eps9mid epson epsonc epswrite escp
   escpage faxg3 faxg32d faxg4 fmlbp fmpr fs600 gdi hl1240 hl1250 hl7x0
   hpdj1120c hpdj310 hpdj320 hpdj340 hpdj400 hpdj500 hpdj500c hpdj510
   hpdj520 hpdj540 hpdj550c hpdj560c hpdj600 hpdj660c hpdj670c hpdj680c
   hpdj690c hpdj850c hpdj855c hpdj870c hpdj890c hpdjplus hpdjportable ibmpro
   ijs imagen imdi inferno iwhi iwlo iwlq jetp3852 jj100 jpeg jpegcmyk
   jpeggray la50 la70 la75 la75plus laserjet lbp310 lbp320 lbp8 lex2050
   lex3200 lex5700 lex7000 lips2p lips3 lips4 lips4v lj250 lj3100sw lj4dith
   lj4dithp lj5gray lj5mono ljet2p ljet3 ljet3d ljet4 ljet4d ljet4pjl
   ljetplus ln03 lp1800 lp1900 lp2000 lp2200 lp2400 lp2500 lp2563 lp3000c
   lp7500 lp7700 lp7900 lp8000 lp8000c lp8100 lp8200c lp8300c lp8300f
   lp8400f lp8500c lp8600 lp8600f lp8700 lp8800c lp8900 lp9000b lp9000c
   lp9100 lp9200b lp9200c lp9300 lp9400 lp9500c lp9600 lp9600s lp9800c
   lps4500 lps6500 lq850 lx5000 lxm3200 lxm5700m m8510 mag16 mag256 md1xMono
   md2k md50Eco md50Mono md5k mgr4 mgr8 mgrgray2 mgrgray4 mgrgray8 mgrmono
   miff24 mj500c mj6000c mj700v2c mj8000c ml600 necp6 npdl nullpage oce9050
   oki182 oki4w okiibm omni oprp opvp paintjet pam pbm pbmraw pcl3 pcx16
   pcx24b pcx256 pcx2up pcxcmyk pcxgray pcxmono pdfwrite pgm pgmraw pgnm
   pgnmraw photoex picty180 pj pjetxl pjxl pjxl300 pkm pkmraw pksm pksmraw
   plan9bm png16 png16m png256 png48 pngalpha pnggray pngmono pnm pnmraw ppm
   ppmraw pr1000 pr1000_4 pr150 pr201 ps2write psdcmyk psdrgb psgray psmono
   psrgb pswrite pxlcolor pxlmono r4081 rpdl samsunggdi sgirgb sj48 spotcmyk
   st800 stcolor sunhmono t4693d2 t4693d4 t4693d8 tek4696 tiff12nc tiff24nc
   tiff32nc tiffcrle tiffg3 tiffg32d tiffg4 tiffgray tifflzw tiffpack
   tiffsep uniprint wtscmyk wtsimdi x11 x11alpha x11cmyk x11cmyk2 x11cmyk4
   x11cmyk8 x11gray2 x11gray4 x11mono xcf xes
Search path:
   . : /usr/share/ghostscript/8.61/lib :
:

I'm guessing I'm missing some libraries somewhere but they are not showing up in the configure.

Can anyone help?

Thanks,

---

### Post by horrendo on 2008-08-28
Any ideas anyone?

---

### Post by blattengel on 2008-09-08
Silly question- Have you read though the documentation included for the latest ghostscript?  The help files are where you extracted the archive to: ghostscript-8.63/doc/index.html  It gives directions on compiling and installing ghostscript for linux.

Also why do you need help if no errors are being shown?  What exactly is the problem?

---

