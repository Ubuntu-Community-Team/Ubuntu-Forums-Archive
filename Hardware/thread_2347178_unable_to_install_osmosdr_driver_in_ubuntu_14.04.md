---
title: "unable to install osmosdr driver in ubuntu 14.04"
date: 2016-12-22
forum: Hardware
---

### Post by koyel on 2016-12-22
Hi,

I am using ubuntu 14.04 and I have installed gnu radio using *sudo apt*-[I]get install gnuradio  
[/I]which automatically installs gnu radio version 3.7.2.1

When I follow the instructions given in the following website

[http://sdr.osmocom.org/trac/wiki/rtl-sdr](http://sdr.osmocom.org/trac/wiki/rtl-sdr)

to install osmosdr driver

as follows

mkdir build
cd build/
cmake ../
 Now cmake should print out a summary of enabled/disabled components. You  may disable certain components by following guidelines shown by cmake.  Make sure the device of your interest is listed here. Check your  dependencies and retry otherwise. 
 -- ######################################################
-- # gr-osmosdr enabled components                         
-- ######################################################
--   * Python support
--   * Osmocom IQ Imbalance Correction
--   * sysmocom OsmoSDR
--   * FunCube Dongle
--   * IQ File Source
--   * Osmocom RTLSDR
--   * RTLSDR TCP Client
--   * Ettus USRP Devices
--   * Osmocom MiriSDR
--   * HackRF Jawbreaker
-- 
-- ######################################################
-- # gr-osmosdr disabled components                        
-- ######################################################
-- 
-- Building for version: 4c101ea4 / 0.0.1git
-- Using install prefix: /usr/local
I get errors after cmake that a gnu radio version 3.7.8 is required but I don't get version 3.7.8 if I use *sudo apt*-[I]get install gnuradio   

[/I]I also had to use the command sudo *apt-get install gnuradio-dev *to solve another issue and after that doing cmake ../ as given above gives the error about the version.


Even though the website says "[B]The Gnu Radio source requires a recent gnuradio (>= v3.7 if  building master branch or 3.6.5 when building gr3.6 branch) to be  installed."

[/B]version 3.7.2.1 is not accepted by cmake. It seems the website is not updated. So what's the solution to be able to install osmosdr drivers in ubuntu 14.04 having gnu radio version 3.7.2.1 ???

Regards,
Koyel

---

