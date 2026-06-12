---
title: "acer travelmate 290E modem"
date: 2007-03-07
forum: Hardware &amp; Laptops
---

### Post by chelala on 2007-03-07
Hi I've read this compatibility list and someone says could install internal win-modem in a laptop very similar to mine.

page is in german [http://home.arcor.de/stefan._lange/linux/acer_travelmate_292lmi_debian.html](http://home.arcor.de/stefan._lange/linux/acer_travelmate_292lmi_debian.html)

in english through google:
The drivers for the internal modem need the Debian package slmodem daemon and either the ALSA-i8x0-Modemtreiber, or the alternative driver which can be found in the Pake slmodem SOURCE. The modules can be loaded without error messages, I it however did not create to develop a connection. 

it means the modem can work ? done know too much linux. help please. Is all I need to have my laptop fully ubuntu

Harold Chelala

PS
translated in google is [http://translate.google.com/translate?u=http%3A%2F%2Fhome.arcor.de%2Fstefan._lange%2Flinux%2Facer_travelmate_292lmi_debian.html&langpair=de%7Cen&hl=en&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools](http://translate.google.com/translate?u=http%3A%2F%2Fhome.arcor.de%2Fstefan._lange%2Flinux%2Facer_travelmate_292lmi_debian.html&langpair=de%7Cen&hl=en&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools)

it says about de modem in german: 
Die Treiber für das interne Modem benötigen das Debian-paket slmodem-daemon und entweder den ALSA-i8x0-Modemtreiber, oder den im Pake slmodem-source zu findenden alternativen Treiber. Die Module lassen sich zwar ohne Fehlermeldungen laden, ich habe es allerdings nicht geschafft, eine Verbindung aufzubauen.

---

### Post by Freiburg05 on 2007-03-07
Hi there, 

     It means that you need the package sl-modem-daemon and of the other two packages:
 
                 1. sl-modem-source: Repositories say (in the information for the sl-mode-daemon package) that if you install this package you have to build the needed separate packages for the modem by yourself after install this package. If this is troublesome for you try with the second package.

                 2.  Intall Alsa drivers: I'm not sure which package you need and which not, some of them probably you already have but I think these ones should make it:
                                  -    alsa-base
                                  -    libesd-alsa0
                                  -    libasound2
                                  -    alsa-utils

                      Maybe you can find better information about how to install alsa drivers in its web:  [http://www.alsa-project.org/]("http://.alsa-project.org").

           
                  You can install all packages above using synaptic package manager.

   
           Hope it helps, although the guy who did the guide you read says he hasn't get it. If it doesn't work maybe someone knows a bit more than me,

             Cheers!

---

