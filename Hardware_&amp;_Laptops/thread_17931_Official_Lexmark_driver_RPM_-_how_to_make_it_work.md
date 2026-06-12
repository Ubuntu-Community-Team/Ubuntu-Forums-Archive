---
title: "Official Lexmark driver RPM - how to make it work"
date: 2005-03-03
forum: Hardware &amp; Laptops
---

### Post by Stefan_hb on 2005-03-03
Hi,
please excuse my english, it's not perfect.
I switched from Mandrake to Ubuntu, and I really love it. The only thing that's not running perfectly yet is my printer, a Lexmark Z53 inkjet.
I have already installed the cups-gimp-print drivers to be able to print at all, but the result is much worse than with the Linux-driver that Lexmark offers for this printer. They offer this driver only as RPM, under Mandrake I could use them, the results were really good (as good as using the printer with windows - as good as they should be.) 
Can I somehow transfer the content of this RPM-driver to my ubuntu-installation? I know about alien, but using google, I found boards in which people didn't manage to get the driver working just using alien, so that probably won't help me.
Can't I just copy the files in the RPM to the specific locations and than somehow install a printer using these files as a driver?
Here is a list of a the files included in the lexmarkz53-1.0-9.i386.rpm:
--------
./usr/bin:
lexmarkz53  lxsetconf

./usr/local:
bin  lexmark  lib
./usr/local/bin:
lexmarkz53  lxsetconf

./usr/local/lexmark:
lxsetconf  z53

./usr/local/lexmark/z53:
A4.xpm          cartcmy1_4.xpm   cartkcml7_8.xpm  Envelope_#10.xpm    Letter.xpm    pqnorm.xpm
A5.xpm          cartcmy1_8.xpm   cartkcmle.xpm    Envelope_6_3-4.xpm  lexmarkz53    ptcoated.xpm
A6_Card.xpm     cartcmy3_4.xpm   cartkcml.xpm     Envelope_7_3-4.xpm  LGPL          ptgloss.xpm
align.xpm       cartcmy3_8.xpm   cartpblk1_2.xpm  Envelope_#9.xpm     license       ptgreet.xpm
alignz53        cartcmy5_8.xpm   cartpblk1_4.xpm  Envelope_B5.xpm     license.txt   ptiron.xpm
B5.xpm          cartcmy7_8.xpm   cartpblk1_8.xpm  Envelope_C5.xpm     lxacalgn.out  ptplainp.xpm
Banner_A4.xpm   cartcmye.xpm     cartpblk3_4.xpm  Envelope_C6.xpm     lxacgsparm    pttransp.xpm
Banner.xpm      cartcmy.xpm      cartpblk3_8.xpm  Envelope_DL.xpm     lxacphal.out  query
Baronial.xpm    cartkcml1_2.xpm  cartpblk5_8.xpm  Executive.xpm       lxactstc.out  rmlp
bbialign.xpm    cartkcml1_4.xpm  cartpblk7_8.xpm  haligncy.xpm        lxaucln.out   salzUS.lut
capcol.xpm      cartkcml1_8.xpm  cartpblke.xpm    halign.xpm          lxauphcl.out  valigncy.xpm
capkcm.xpm      cartkcml3_4.xpm  cartpblk.xpm     httable.bin         Postcard.xpm  valign.xpm
capstdm.xpm     cartkcml3_8.xpm  cbialign.xpm     Index.xpm           pqdraft.xpm   z53
cartcmy1_2.xpm  cartkcml5_8.xpm  colorsV.lut      Legal.xpm           pqhigh.xpm    z53.sh

./usr/local/lib:
libvdkcompo.so    libvdkcompo.so.1.2.5  libvdkgnome.so.1      libvdk.so    libvdk.so.1.2.5
libvdkcompo.so.1  libvdkgnome.so        libvdkgnome.so.1.2.5  libvdk.so.1

./var:
spool

./var/spool:
lexmark
------------
I would really appreciate help, because getting good prints is one of the most important things to me (computer-concerned, if you know what I mean :) )

Greetings
 Stefan

---

### Post by OSHEACVA on 2008-06-06
usr/bin
lexmarkz53 lxsetconfi
usr/local
bin lexmark lib

---

