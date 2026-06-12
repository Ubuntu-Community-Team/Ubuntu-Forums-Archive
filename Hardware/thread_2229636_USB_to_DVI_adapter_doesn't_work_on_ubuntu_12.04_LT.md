---
title: "USB to DVI adapter doesn't work on ubuntu 12.04 LTS"
date: 2014-06-14
forum: Hardware
---

### Post by Timothy_Leung on 2014-06-14
I tried to connect a second monitor to my hp PC so I bought a USB to DVI adapter from ebay last week. 
The model is this one 
[http://www.ebay.com.au/itm/USB-2-0-TO-DVI-HDMI-VGA-MULTI-DISPLAY-GRAPHIC-ADAPTER-CONVERTER-WIN-MAC-LINUX-HD-/171041044468?pt=AU_CablesConnectors&hash=item27d2d737f4&_uhb=1](http://www.ebay.com.au/itm/USB-2-0-TO-DVI-HDMI-VGA-MULTI-DISPLAY-GRAPHIC-ADAPTER-CONVERTER-WIN-MAC-LINUX-HD-/171041044468?pt=AU_CablesConnectors&hash=item27d2d737f4&_uhb=1)

I am using hp Pavilion 23 core i5
[http://h20565.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay?javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken&javax.portlet.prp_ba847bafb2a2d782fcbb0710b053ce01=wsrp-navigationalState%3DdocId%253Demr_na-c03524666-13%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.tpst=ba847bafb2a2d782fcbb0710b053ce01&ac.admitted=1402755020466.876444892.492883150](http://h20565.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay?javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken&javax.portlet.prp_ba847bafb2a2d782fcbb0710b053ce01=wsrp-navigationalState%3DdocId%253Demr_na-c03524666-13%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.tpst=ba847bafb2a2d782fcbb0710b053ce01&ac.admitted=1402755020466.876444892.492883150)

I tried to follow this post 
[http://how-to.cc/get-a-displaylink-video-adapter-working-with-ubuntu-12-04](http://how-to.cc/get-a-displaylink-video-adapter-working-with-ubuntu-12-04)

Whenever I tried 
apt-get install[COLOR=#444444][FONT=Consolas] [/FONT][/COLOR]xserver-xorg-video-displaylink

I got the message
The following packages have unmet dependencies:
 xserver-xorg-video-displaylink : Depends: xorg-video-abi-11
                                  Depends: xserver-xorg-core (>= 2:1.10.99.901)

Then I tried to apt-get install both of them

After installing them and reboot. It directly go to terminal mode instead of GUI mode. I tried ctrl+alt+F7 but I cant return to GUI either.
I have to reinstall ubuntu again. I tried this three times already and still getting the same problem. 
I guess there is a bug? 

Is there any other ways to make my usb to dvi adapter work?

---

