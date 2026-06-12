---
title: "Retrieve data from tape"
date: 2014-02-19
forum: Hardware
---

### Post by Tanio_Artino on 2014-02-19
Hi All,

I would like to have some help in opening old backups from an old magnetic tape. I have looked around and the guidelines but I have not found anything that might have helped me to overcome this problem.

I possess an old Tape Drive (Sony SDT 11000) and some old tapes.
I would like to retrieve the data from these tapes, therefore, I had a look online and I used the following commands:

My device is at /dev/st0

1 ) Rewind the tape
**mt -f /dev/st0 rewind**

*Terminal*:

2) To find out whether the process was successful I executed the command: 
**mt -f /dev/st0 tell**

*Terminal*: At block 0.

3) I do not know the format of the data inside the tape so I tried some attempt with the tar command

**tar -tzf /dev/st0**

*Terminal*: tar (child): /dev/st0: Cannot read: Cannot allocate memory
tar (child): At beginning of tape, quitting now
tar (child): Error is not recoverable: exiting now


gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error is not recoverable: exiting now

4) Never give up :) so I thought was a problem due to other reasons 
[B]mt -f /dev/st0 status 

[/B]*Terminal:*SCSI 2 tape drive:
File number=0, block number=0, partition=0.
Tape block size 0 bytes. Density code 0x26 (DDS-4 or QIC-4GB).
Soft error count since last status=0
General status bits on (45010000):
BOT WR_PROT ONLINE IM_REP_EN
 
5) Many forum report this problem like a memory allocation problem, therefore I tried this:
[B]tar -t --blocking-factor=128 -f /dev/nst0

[/B]*Terminal:*tar: Record size = 64 blockstar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors

6) Bad luck so I tried this command
[B]mt -f /dev/nst0 setblk 0

[/B][I]Terminal:

7)Again status
[/I]**mt -f /dev/st0 status***Terminal:*SCSI 2 tape drive:
File number=0, block number=2, partition=0.
Tape block size 0 bytes. Density code 0x26 (DDS-4 or QIC-4GB).
Soft error count since last status=0
General status bits on (5010000):
 WR_PROT ONLINE IM_REP_EN

HEEEELLLLPPP :)

Please can you help me to access the tape

---

### Post by TheFu on 2014-02-19
Until you know the format/program used to write the data and find a compatible version, this will not work. There are hundreds of programs.
tar, dump, dd, ufsdump, netbackup .... 
Don't forget that the "indian-ness" matters too.  So a tapes created from an Irix box have the bytes swapped compared to a SunOS box. The command used to retrieve that data will change accordingly.

So - 
* what program and version was used to make the tape?
* which OS was used?
* was HW encryption enabled?

If you don't know it - try go pull the first 1K of data using DD and look for headers to help out.

---

### Post by Tanio_Artino on 2014-02-20
Thank you for you answer

The only think I know about the tape is that it was compressed using hw compression and the original file is 8 times bigger than the file stored in the tape.

I have followed your suggestion and I executed the dd command as below

[B]dd if=/dev/st0 bs=32K of=header1

[/B]*Terminal:*
5016+0 records in
5016+0 records out
164364288 bytes (164 MB) copied, 75.1117 s, 2.2 MB/s

I have got a file that I do not know how to open

any suggestion?

---

### Post by Tanio_Artino on 2014-02-20
Update[B]

dd if=/dev/st0  bs=32K  count=1 | strings [/B]

*Terminal:*
ON-LINE Backup Header.
0880
1+0 records in
1+0 records out
32768 bytes (33 kB) copied, 3.59893 s, 9.1 kB/s

---

### Post by TheFu on 2014-02-20
What does "file header1" say?

---

### Post by Tanio_Artino on 2014-02-20
It is a file of 165 MB. I opened it with vi 
here the first part

^VON-LINE Backup Header.^@^@^@áÌ1^AûyÉ^@^D0880^@^@^@^@Uñ.^D^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@áÌ1^AõyÉ^

in the middle

AO<^D8@?|ÌÜ3^L^M^@Â^O#@^@^CÀ^M^HCÂ^Lò4ó^LÁ^L   ^L^OÃ^A?Í^Pð^_Ì7ð<^A^HÃL^@#L^L^O1ãÀ|^@pÀÀ^@4=Ü^C^L^A^Oý^@Í^S^O<80>ÀÄ3ÁÀ<80><80>À3Ä8^\<^@|^C0^A^O^N<^BÓ^@÷0^HÀ^\¼^C4 ^Ló0^D^LCÃÍ7^@<80>|ð^H^@s°À^?ó4#^@<<80>^DüpÀ^Lã ^L^@Ì^DÂÇ^L@^C^P?^_0^B^O^@;^MÃ^DðÍ^S^O^O=ò@<CÀ?=^H3^@^D3^_p^B0Cð^O^ML|^OpÏ^\<^@ìÜ^L^C^D^H^@^H^@^_3'^@^O^OC·^L^OÜ^B^L<ÇÀ^BÜ^@2^@O^BðÀ^S^LÀ^ML^C³p^C0^D0À^M^L^H^@^B^@ï1^L^@ö^L^@p<8f>^@<^@^C^RÃÓ^H^@^K^@^BÃ<80>^@Ì`0^?³^@Ã^BÀ^O^@Ä !Ì^L7#Ó<ü4ÏÄ^C^B^@Ë=0<10ñ#^@Ì^BÀ=^LÁL^C8Ó^@/^L<80>^CÄ<p^@Â^C^BÃ^M^O<^D^GÀ8Í<80>ÃÀ^LÁ3Á^C'^@Ì ^Cñ^BÀà^@¼^M<^H0^_^@3Ä0ñ^B^CL<80>LÌ ^C3ÜÃÐ^@|^C8pÃ^@^LM^C^C^Pü^P?|À^B^GÃÂ^@ð  ð^H^@Ïñ^@^H^@1<83>^@ 0ð#<80>ð^LC^@<9c>^@8À=^C^L<8c>^M3^S³^C4ó^M^Lð^CÐôÃ^SÈÀ^@<87>^C0|^HÏ1^@0ÇÁ^CÜ<1<80>^L÷|3^@;^@^@^_0<84>À^?<83>^L^Cs^C C^O^@^@ÜÄ0^L^M0<80>7ÀË^SÏÏÁ¼1<^_^Op^C^@^G^C@^H^L?^D³^@|^H^O^@ó^]Ã^CÄ^L^@Ï^A^C1^^^L<80>^@÷^G^CÌ@ÃL^BÀ ^@^LÃÄ8^@ð!^C^LsÃÈ4^CÃ^P^?À^O$^C^C^S<83>Ç^@^BóßÀ^L^@^S^C^M^_^L^GÂ^@ÏÍÀ^D3^PüÄ^C^M^L^P3^L4;ÇðK^LÏ^Cs^@/1^CÌ^D^K0^@L^L^P<80>0LÌÃ!<ÍC3<Ì^A<83>0@Ì^HÄÃ^S03 Á<L0^@<83>^P0L^O^\3Ä^@~ÏpÀ^C31C<^?ÌÄð^O^\¼À^M°^L^@^C1ðÞ^@^@^K^H^C^@#l3^O^CÈ^\3^Lñ^@^H^@<ñp<^RÃË^PÏ^P3^B0^?^LO^O^O@^Bð^L4<C0^K=^O^P3^D^Lô^@ÃG^O^P^C^@7#^@^OÌs^@Ü÷7ü^\^O8^C^\<^PÃ4ÃñÀ^A<8c>^@Ð3^@·0^@0^MÀ ^L!ð^@?4#03^? <80>À^G^H?^\^L^B3ÄÌÌ^P^@Á^CÄ^@^BÀ3@ ^@¼^@ô0Ð0^\¼^@ ^@?^@Â0<80>^M3,|^LÌ@^CÓ031 ^@^CÆ<^@0^[<^C<90>^@3<80>=ÀÀÀ7È^@<80>^\^K^OßÀã^C?Á^@^H^P<83>^@Às^@<82>^@ð^C^@À<87>^@0`^O^C Ü^Ll^O<^L07^L^B^L4Ì^H^G^OÂÜ0^L2^Dü^P2ð<^PóÆ<^@^LÂÄ^@ÂÀÀ^MNð^@^@,^PÈ^L^L^@(À ^@^Cð1^@¼^P^BÌÈL^O^@Ì=<80>^Mó^G3^C0LÌ=^Aÿ^LÄL<L^O^H^@Ã^A^C<80>^S3^\^K^L^CLËCÃ3C^@^L7<80>0ñ^@ø13^M^C<1¼^\<^GÎ^@^LÐ0^Cp 0^H^@#ül^CÀ8^S<^C^H^Hü^@ÍpÏ^C^G^OÁL^CÏÁ^@^D ^@^S^HÌ0^P^NÀ^_<Có0^Að^Gß^G3^@7¼^LÀ^NÇÌ^DÎ0À^CÆü43#ÏOÌÂ^D0C^@xð0<81>ü^@Ã4^LÁÃÁÎp^@^O^P^C#^@^MÀÐ^L7ÏÆÀ^Lô<Ü^@^@H^O<80>0^C<81>Ì^GÏ^@=<80>3^L^G/ÀÀ^H^D^L#Ì^\^@^H^Ls<^@<81>0^@^@^L-^@3sp;^@,À<8c>7Ã^@^H^C^\0O3OÀ^H^@20^@Ü^L^@7Ð^CÇÀ <80>^@Â^SÂÃð ^@^C^B^L^G Ð?^G^O^SÃ0^H^O<8d>^L34^LC3^P?CüLÀ73^A^O^B^L<80>^@^B^@^@^\<83>À^BÀ0^@@<ÜCÃ^@^N7ÏÁ^OØ ^C<<^M^C<^P^L^BØÏ^@^O^B<83>À^D3Ã^@À<8d>^@ÈÐ3À^@^B^L,Ä<83>^@0^C^\0w?C°^L<80>À°^@^C^C<80>^@^CB^OÜÌ|^CóH^LÌ^NÄÂÀs^LO^C<à3ÈñL^OÀCÈ^LLÀÌ<81>^@3^BÁ^O^L÷ÌN<80>3^@?^BÓ^OÀ^GÜ^L^DÌ^[Ã^@^S^L^@÷0^D<80>^B0^@^@ðÁ!^C^LL2Ó<sÏ^@ ^C^Cp^@K^C^O^^ü^@^O^_ÃÃt#^@#00^\ ^L<84>^Cð^C^@^GÃ^D^O,ÐÀ#<80>À^CÃ^C^D2^L;@3³CÏ^@Í2^@^O,C<80>^C^CÌÇÇ<8d>ð^LL<Ó^@ Ì^D^LC^@CóL^Là^M^@3Á2^@È^@ ^Lø^A8^@?1À4ÈÃ^PÏ^P^LÌÁ^Lôð!^@?ÆÌÌÀÒ^@^C^HÃ^AÂ^L@ÌK^C^Os?Ó^O^PÏ4^@ò0^G<8c>ÏÄ^@^K^@^BðÄ'^Lü^@^M^L@ÀÎÐ^Cß^_Ã^B^O@3^@rÃ^C^Aà^CÜ^@ ^LÀ^LÄ<80>^@4ÃÍp^OÐ^CÃ <8c>ð|3Ï<87>^C03^@^A^M|È^SÏ0^@^M sÀð!0ÀÌ^M^@p0L^L÷À|^C^S ðÀÄ^O^BË^Gó^DÌÓ0^\<^CÁ^\^Bà^Sð^CÀ~^L3Ä<^G<80>^L<80>|<À^CÄ<83>0LàÀ^LÍO^@L^Lp^CLÃ^L^HH^L<^L^M7Ì^D^O^M04^@ ^L^@7^HÀC<23^\^K^LÀ@^O^P0L^C^N7,^LÀÓ^@ÌG?p<Â0^@rÀÏp^@ð@^Lp^C^Pó<9f>^CÌ^\<80>ÏÍ^@Ã^P^Oø^M^C^GÏ^K^SÌ@^CÌôÃñ@ÏÓÀ^@CÀÂ1^H<^@0Í^P3^L^G^@^L^M^Hðý@àC<83>^Lü^@=^@ó<90>0<80>03^Fà^C<80>^C^@^C^B^C^P/^@3^@à^D^O^F?@3Ã^X<8f>^@<8f><^@C^C^CÐßÏÍ0^@^H^H^C^HÇ^L^C°À^G^@ ^@ÂÀ^H^@;ôÍ^L^C<B<8c>^@^CÓ^@^B3<9c>^C3<80>^@ ^@^?^O ü^P8^C0^O44,^@Ã'ðÍð^\ÏÄÀ^G^K^\^OO^@Èp00^L>^A^LL^H0O<80>^@Í^@Ã^CÁr0^OÃ^B^DÏÁ^O^PÌC^@8<80>^M3ÌÄ0Äó=^@<80>L^LÃ^Ss^@2À,Ãô^C8|<^B^@^\0àÀ43ÌÑ^C^@^Cñ^D7óü^DÌ^G>^@^L4p^BßÃð10<10^Ap^L^C^P^HÀ<80>^@<8c>^PÏ^\<83>^C#^B^L<8c>pð^L÷?^MÃ^\0s^_À^H^@,^DóÂÀ^L^M^L^P0^B^_ü^@<81>^C<80>Ló^LÃ¼@<C^C^_^C>ÐðÀ@^@^@Æ^L3#^Pü@^C^C·^@ÀÃÓ=8À<^D^C<87>^LÀp<Óð^\^BÈ^@Ì^@÷^KÀ ^@O^L^C1p^O=@<<8f>^M<^C^D3Ü^@s^C^@<93>^@ <^@È^@2^M^L3^R<83>^CÀ2^@3^M^L^@L^O8^AüÓ008L^@^H^OÜ0^G3^D^O<8c>^@4^L^PÌ^G^K03@^O@^C2^@<80>^C=^B^L8ÐÌ <80>ðñÃÌ@<80>^@^B3<84>ÃÌ^H0^KÀðÇ<80>À^L±0^LÇÀ@óÇÌ4 0C^L^L1^@^_^B0³À1^C0^A¼@ÏÄ^@^B^@ÏÁ34Ì^M,^\Ã^C^O1<KÀ^O^@p^@Ü^L^PÂ<^M0^L^HÀÜ^L^DÂ^@3ß^CÌÁ^BÈ^\ ^C<^CH^C^C^C^@^[^@<83>O0Ã 0Ç^C^L^C1<80>Ð^H0^HÀ<80>sð^LÁ^?3Ìô^O^A<83>^@^L^N^H^O^DóÁ0ñL^@ÎÐÃ^@^M3ÐÌsÀ$À^CÀ^L^M4ð=^@s0@<80>À0à^S^O^@Ì~Ì^L      ð0C3ÁÃ@^L^Cr^@?@^C<80>LóÇ<7Ã^PÏLÀs^@Ì^P0C^O73 =^L^@01Ä ^C{^LÃï^AÏÓðOÃ<8c>^LOÀÓ0^?ðÁð<^Q<È^@ôü^A^C^@ó^A^M^C^MÁÎß^OL^L^C^SÀ^K<80>^@^B3^L^AC^O,ü^M2À0^@^K^\^L<90>^L0À|^@`3^C^Ró^Cðp Ì^M3^P^O^BÀ^O^A<83><80>07^@À^@^C!^L^C<8c>ñ^@³^@^@<-C<^KÀO#Ìð4^@204À^K4^O^@^B^H^L ^@?<80>L^C;Ðü4À^B^@/0^M 0^KÀ^@^S^L^@7^@7^L^SßÓÀÌÜ^?0ÿ!0^@^C^C^B^HCÃ^L^M^HÇ<^@<8c>^DÃ^@p#^@<^@^H^@^L±À ð^MË^@^BÃÓÀÌH3°^L^O^M^@ì4<^@^LÍ@Ã<80>Á00^MÀp<80>^\ðÌ3^A?^A^L^Bàp30^BÌpÏ40p0^Sà^@^L2^@^B^H<CÌ^\ð°^A3^@ÌÐà^P?^@À^@@À{^C^L^_^O^D^O^HÀ^@À0^A{À<^SÃ^@4^L6Ì0^B^L6<#0Ï^D^Op^L^L^M<83>^L=l3^CÀ<80>^L^LÜ^C^HÀ^_^@ÃÄ<ÉLÃ<83>00Á^OÌÁ0^@^HÿÜ^A^O^H^L<80>^@^B^BÃ^@=^S¼ð4Ì^@^_ ^L0^@4^K43^Kñ^O<84>Ì^@<4<p^L^A³<13s^C8^@L³^@0^BÀÇ0Ä^CÄ^C^DÂ^@^Lô^@^\^C^B^HÀì^\Ã^O^A^OÀ^M0ÂÜ0^C^RÏ^@°ÐÀ^@04s^@^OH^O^C^H^C¼Ü0<80>^@^C^Bó^A <Ç00ÁsÌ^C^@4^BÀ<80>^\Ï@ð0Í0^DÂÐ0<80>À^L@ø1,À0À<80>pÌ^C^@<90>^L0^H ðÌÁ 0À^Bà^@Àß^@|ÀLÏl ^L^LÏ=^CÜð^@Í ^LC^O<^A^LB^CÏ|^@^C6À^Lc0^?^@<8f>^@ ðý=^L^O1^B0^C<80>^@4#À0pü@ðC^CL^CCÀs^C^\<ß0^@^@^A^H^L^L60^@<8f>^Mü^A?Û^CÌ^CÆ<0p8^@32^C1^O^BÀ^S^C^C^B1^H^@,Às<80>^O^@#÷^C ÀÇ^Cpü^H^H^@^C^B^HÃ=00^P0^K$Ì^@"ÀÌÌ1 ^C=^BÀ<83>^@ 0^L^@K,^@#^C<ÃL^L@3-^@<L3ÀL^\>Ä<L^O03ý@^O@ðþ1ü^M^LÃ1^Hð1^@À17ÃÀ1^C^M^\ó^P^@>Çð0^Bð1À^D^C<90>^@00Ðs0#^@^L^HÀHó^@0^_ÀcÃ^L^@3!0ÌH^LÃ4^CCÌ°^G3<80>ôÀ^CÜ^@8ÐÃ7À^L1#<Í0^O^\^@^P^@^B8À^@<ÁpÌ^\ß^_ó^@,01Ë^@^NÀü^D^L^N^@Ü ^@0s<80>^LÄ<Ì^ML^H^O^CÒ0^C(^L^LÀ^B^C^_<80>0 2Ü00^L^M<¿^A^L?Áp^L^@^B^P8^@Ï^\0^L^DãñÌ÷OÌÀ^B^\ó^[ÌÀ 0Ì^D<@<^L^A^_0^LðM^O^HðÜ^@LÂ^_ø^L=^C^CÂ^@^AÈÀ3^AðÀ      ^L^NÜ^C<@<^PÏ4ÌÀÁ^Gð#^D,^LÌÀ^P^LCÈCð3^\<83>^C^@^@ÓÐL^CÏ^P^C^C<80>Á^@^L^@Ð`^C3À<9c>^@3ì=^CÃ^L$ðý^@À^[^O^BðÀ@ ÇüÍÏ^AÂ^LÀ^Só^S^OÀKßÀ0Èý^L^@<80>^\Ã34^L^A³^L°^C^S^C^L^P3ßñ0üÁp0øCð^L^A^L<1'^L^L@^Cß0<80>ÀÍL0s<À1È0^M^O@^L ^AÏÐ2^@^H^@^C÷Ó^LCÃ^@<90>3^Ló^F^BÀ^O<81>^CÀ^Cs^K^H^@<8f>^G^C^Oð^M<80>Àp^@ßÀÇ<83>1ÿÁ3pü@^L^@÷<80>^Mó^H^C^\<<83>^@^@<^H!OÌ^@24?ñ<^B<^A37Ì4^L^N^PÃ<80>^@<8f>À3,^\CÀ^@^P3^D^O^LÁ°^@^C^F0^C;Í3^Pð0^A^C8^DÂ^L3^B^SÌ^@|^@^BÀ^GÃ^@^\Ï^D^H3^G^LÂ^Bß^C<80><^@0<9c><^D#Çó<84>Ì^@ ^L^OÜ^LO^L^@C0(ÀÀÀ1þLÈÌ^@ÀxÀ,Ä?^@ð42^M0^@^NÍ^L^_3^L^@=^G<8c>Ó^Lð^@òÁ3Á^@Ï^A ^@<Ä<^A3@^Sã^@^@3 ^@ï7Ì^M<80>°^@^LO^@Ó<ô Ì0ô^L=ÓÀ^D3^P^L^CL^@C^OL<<9c>0^@L^L<80>^@^C<^M0p<80>0Á^CÃ6÷À|ÀÌ^A^HÌ^C^@Nó@0^O|ÌÞ^@^O^LC^S<^CÐ^LÆÌ ^L<8d>^L0^C^LH^C^B0^C8^PÃO3^O^S³^\^C>^D<83>^@ð^LÇ^L^DÏÄ^@^K;ÇÃÇ<^@^@^D^@<81>^LÃ<80>Ó?Í^L|<80>Ï^A^B2À ð3$^@³ÀÀàà^@Ã^MÀp<80>3^@=^G°^@Ï^G^C7Ã^C<81>^@à07^L ^C<^D^C^K4#^@<^@=^@Àpá^@°07<2±0^LÈ^CÐ^LÌÜ<83>^CÀ^MÃ^G^@÷4?^D,^@?|È^C^@^B^C^B=<^D^Cp^@^N<90>0#Ã^H^LÀ,^\ð^@!Â^LÂÌ<^G,0^@ÎÜ^C^N^DðÏ÷,^LüÁ^O^Aü^M^\< ^@<8e>^@ð^M^@Ï^A¼^L<90>Ã^@^@À^_ö^@Ã^H^@C^B<83>^L÷^@ÃÀ^G^SÀÓ^L<90>Ì0Í^O^DÌLÃ<93>^@^CÀ4ópð!À8ñ^Cóó}ðÃ/^P^L^@^M^?Ï^O70^GÈÌÃ^D^@Â^D^O ^@^@^B^G^B^L3À±^L^@ÃÁÂñCÈ^LÈ^S3<^@^\<8c>^@ìÜ^@?^L7à1^LÀ@ð^C^AÂ^@2ÁÌ1Ï^D^O^NÇ^L ^CÁ^@01LÀ^BÀÓ0^H^@2Ä^OÐ^Có^H1ð,^@^H^CÂ´^@^L0ð^DÀ=Ç^C4ÈÍÌ^L0ÁÂ^C^Cô4À1sÃ^C^^3^@^C^K@Ï^HÄð^@=À^Sðs<80> 00^\Ì^C^D?4Ë^A3^@Lð<83>^@Ç0=0^@pp^C^K<80>Àñ00Â^M<80>^C<4°À=^Cï^P^L 0^C<8d>^L7ðÃ^A0^@Á#`^L?@óÓ^Ls<83>30^B^@^Hs^@^OÜHÃ^O^@øÐÃÍ04^L^H^@^@^BôsÃ°0ñð1OÀü0^M@0^@Ã1^Gìpó^P;<Às^C <4ÃÁó^CÓ^H7^@L^L3^D?ßÐÌø^@ÏÅü4ìó^LÓ^A^@à4À,^L^M^C0pÀ^PÂÃC08^S^C^@0Ä^L^D^HÀpOÈ^L^@<83>^@àÓ<^@<83>^@^@Â<80>÷^@ðÂÁ^C^HÀÌÐ^H^C^H^C^Kp3Ó°À=?4^LCÌÀñÀýp^@ÏÄìô0^@ÃÁ@^H^C?^AÌ^@^A÷^@ ÀÇ0<87>ÀÈ^@^KÀÌ|À8Ä<<80>^@Àô0÷<80>Ã1^C=@ÃCà^L^LÍ^H0Àï^A3À1<80>3ÇÏÁ^L}^LÀ0pÀÓpÀÐ^L<80>Ã^D

---

### Post by SeijiSensei on 2014-02-20
```
tar -tzf /dev/st0
```

Since you say the tape was written with hardware compression, using gzip compression with tar is redundant and reduces performance.  Perhaps the tape was written without compression?  What if you omit the "z' and use "tar -tf /dev/st0"?

---

### Post by Tanio_Artino on 2014-02-20
Thank you Seiji

if I run your command this is the result:

tar -tf /dev/st0
tar: /dev/st0: Cannot read: Cannot allocate memory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now



The tape was created with a machine working with windows 2000 professional and these tapes are coming from a logger, which once it was full the data was stored on tapes. To be honest I am expecting a strange format. I have spent three days to understand how to read the header to gain more info but I couldn't. The only info I have is:

ON-LINE Backup Header.
0880
BSVR

So far only the dd command has retrieved data on the tape and although the data is readable I do not know ho to open the file created by the dd command.

Any suggestion?

---

### Post by TheFu on 2014-02-20
You need the Win2000 OS and the exact same program used to write the data to get it back into any usable format. Seems like an important detail to mention.

Is anything written on the tape case to provide more clues for the actual software used?

---

### Post by Tanio_Artino on 2014-02-20
Thank you The fu

Right now I am working on installing again the old system and some applications to extract the data, so I will be able to retrieve the data from the tape soon. However, the purpose of this tread is not to retrieve the data from the original software (its performance are extremely bad) but I want to retrieve the data without this software and using parallel drives at the same time. I do not have the API of the original software but I was assured that the data inside the tape is not encrypted but only compressed with hw compression with a ratio of 2.1
Therefore I believe that if I get the right compression format and helping myself looking at the contain of the data using the old system, I will be able to create my extraction software. 

What do you think? Is this an achievable solution?

Moreover, I would first copy the tape on a disk file (with dd), then use file command on that disk file
Do you know how to do it?
I tried this but it stops when the block finishes
**dd if=/dev/st0 bs=32K of=tapecopy**

---

### Post by TheFu on 2014-02-20
There is little reason for proprietary software to use open data formats. I wouldn't expect any commercial backup software to be any different when storing data.  They want vendor lock-in. The combination of tape hardware and software provide powerful lock-in.

I think you want the count parameter to dd.  It will be slow with small block sizes.  Reading the tape needs to use the same blocksize as it was written using. At least that is what I remember - haven't used a tape drive in about a decade.

---

### Post by Tanio_Artino on 2014-02-21
Thank you very much for your help

What do you mean when you say that I want the count parameter to dd?? the blocksize is 32728 so I think is not going to be slow :)
I have got support to achieve the tape conversion but I do not know what to ask. Can you help me to create a roadmap on how to achieve this?
I have heard about the MagicNumber, can it be useful? 

Thank you

---

### Post by TheFu on 2014-02-21
> **Tanio_Artino said:**
> Thank you very much for your help

What do you mean when you say that I want the count parameter to dd?? the blocksize is 32728 so I think is not going to be slow :)
I have got support to achieve the tape conversion but I do not know what to ask. Can you help me to create a roadmap on how to achieve this?
I have heard about the MagicNumber, can it be useful? 

Thank you

A parameter is a option to the program, usually passed in AFTER the program name.  You are already using 3 parameters, if, of, bs.  I think you need to add "count".

**man dd**
will pull up the manpage which explains. Every command on Linux has a manpage - which explains all the options/parameters to the command.

I don't understand what you mean by "roadmap."
To read the tape, you need the OS and program used to write to the tape configured, connected, in the way it was the day the tape was written. It might be possible to use a different OS, if the program is compatible.

Magicnumbers are what the "file" command looks at in the header.  I asked you to run that program previously, but you haven't.  All these programs are run from a terminal.

---

### Post by Tanio_Artino on 2014-02-21
Thank you for your help.

If you see the previous discussions I have already used the command count various times. This is the reason why I asked you what you mean for count (see previous page). I was a bit confused for this reason.
As regards the file command this is the first time I hear about it. I am going to try it soon and let you know.

When I say roadmap I mean just a process to follow to achieve a result

I would like to say again that I have really appreciated your help :)

---

### Post by TheFu on 2014-02-21
count=1 gets 1 block.
count=20000000000 might get the entire tape ... but without knowing the format from the program, it is just raw, unusable data.
There isn't anything more I can help with here. Sorry.

---

