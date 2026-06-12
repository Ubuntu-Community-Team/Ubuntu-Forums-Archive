---
title: "gphoto2 + Canon EOS Digital Rebel XT"
date: 2011-05-04
forum: Hardware
---

### Post by Ponderomotive on 2011-05-04
Hello,
Trying to get gphoto2 CLI to connect to Canon EOS Digital Rebel XT camera. It seems to identify the camera but can't talk to it. --debug below.  Ubuntu 10.10. 

Any help appreciated!  

===================


~$ gphoto2 --summary --debug
0.000053 main(2): ALWAYS INCLUDE THE FOLLOWING LINES WHEN SENDING DEBUG MESSAGES TO THE MAILING LIST:
0.000108 main(2): gphoto2 2.4.5
0.000119 main(2): gphoto2 has been compiled with the following options:
0.000127 main(2):  + gcc (C compiler used)
0.000134 main(2):  + popt (mandatory, for handling command-line parameters)
0.000142 main(2):  + exif (for displaying EXIF information)
0.000149 main(2):  + cdk (for accessing configuration options)
0.000156 main(2):  + aa (for displaying live previews)
0.000163 main(2):  + jpeg (for displaying live previews in JPEG format)
0.000170 main(2):  + readline (for easy navigation in the shell)
0.000181 main(2): libgphoto2 2.4.8
0.000191 main(2): libgphoto2 has been compiled with the following options:
0.000198 main(2):  + gcc (C compiler used)
0.000208 main(2):  + ltdl (for portable loading of camlibs)
0.000215 main(2):  + EXIF (for special handling of EXIF files)
0.000224 main(2): libgphoto2_port 0.8.0
0.000233 main(2): libgphoto2_port has been compiled with the following options:
0.000240 main(2):  + gcc (C compiler used)
0.000247 main(2):  + ltdl (for portable loading of camlibs)
0.000254 main(2):  + USB (libusb, for USB cameras)
0.000261 main(2):  + serial (for serial cameras)
0.000268 main(2):  + no resmgr (serial port access and locking)
0.000276 main(2):  + no baudboy (serial port locking)
0.000283 main(2):  + no ttylock (serial port locking)
0.000290 main(2):  + no lockdev (serial port locking)
0.000297 main(2): CAMLIBS env var not set, using compile-time default instead
0.000304 main(2): IOLIBS env var not set, using compile-time default instead
0.000337 setting/gphoto2-setting.c(2): Creating $HOME/.gphoto
0.000423 setting/gphoto2-setting.c(2): Loading settings from file "/home/john/.gphoto/settings"
0.000641 main(2): The user has not specified both a model and a port. Try to figure them out.
0.000666 gphoto2-port-info-list(2): Using ltdl to load io-drivers from '/usr/lib/libgphoto2_port/0.8.0'...
0.000790 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.8.0/disk'.
0.001139 gphoto2-port/disk(2): found fstab fsname proc
0.001185 gphoto2-port/disk(2): found fstab fsname UUID=99562878-247a-4bca-bfb0-949b7dd6e964
0.001203 gphoto2-port/disk(2): found fstab fsname UUID=a19cd7f4-5917-4bf2-9377-12c4562358ed
0.001251 gphoto2-port/disk(2): found mtab fsname /dev/sda5
0.001269 gphoto2-port/disk(2): found mtab fsname proc
0.001287 gphoto2-port/disk(2): found mtab fsname none
0.001308 gphoto2-port/disk(2): found mtab fsname fusectl
0.001318 gphoto2-port/disk(2): found mtab fsname none
0.001342 gphoto2-port/disk(2): found mtab fsname none
0.001363 gphoto2-port/disk(2): found mtab fsname none
0.001381 gphoto2-port/disk(2): found mtab fsname none
0.001400 gphoto2-port/disk(2): found mtab fsname none
0.001418 gphoto2-port/disk(2): found mtab fsname none
0.001437 gphoto2-port/disk(2): found mtab fsname none
0.001456 gphoto2-port/disk(2): found mtab fsname binfmt_misc
0.001481 gphoto2-port/disk(2): found mtab fsname gvfs-fuse-daemon
0.001493 gphoto2-port/disk(2): found mtab fsname /dev/sdc1
0.001513 gphoto2-port/disk(2): found mtab fsname /dev/sdb1
0.001530 gphoto2-port/disk(2): found mtab fsname /dev/sda1
0.001898 gphoto2-port-info-list(2): Could not load port driver list: 'Unspecified error'.
0.001917 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.8.0/ptpip'.
0.002123 gphoto2-port-info-list(2): Loaded 'PTP/IP Connection' ('ptpip:') from '/usr/lib/libgphoto2_port/0.8.0/ptpip'.
0.002144 gphoto2-port-info-list(2): Loaded '' ('^ptpip') from '/usr/lib/libgphoto2_port/0.8.0/ptpip'.
0.002155 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.8.0/serial'.
0.002457 gphoto2-port-info-list(2): Loaded 'Serial Port 0' ('serial:/dev/ttyS0') from '/usr/lib/libgphoto2_port/0.8.0/serial'.
0.002473 gphoto2-port-info-list(2): Loaded 'Serial Port 1' ('serial:/dev/ttyS1') from '/usr/lib/libgphoto2_port/0.8.0/serial'.
0.002485 gphoto2-port-info-list(2): Loaded 'Serial Port 2' ('serial:/dev/ttyS2') from '/usr/lib/libgphoto2_port/0.8.0/serial'.
0.002495 gphoto2-port-info-list(2): Loaded 'Serial Port 3' ('serial:/dev/ttyS3') from '/usr/lib/libgphoto2_port/0.8.0/serial'.
0.002505 gphoto2-port-info-list(2): Loaded '' ('^serial') from '/usr/lib/libgphoto2_port/0.8.0/serial'.
0.002515 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.8.0/usb'.
0.003356 gphoto2-port-info-list(2): Loaded 'Universal Serial Bus' ('usb:') from '/usr/lib/libgphoto2_port/0.8.0/usb'.
0.003375 gphoto2-port-info-list(2): Loaded '' ('^usb:') from '/usr/lib/libgphoto2_port/0.8.0/usb'.
0.003386 gphoto2-port-info-list(2): Loaded 'Universal Serial Bus' ('usb:002,003') from '/usr/lib/libgphoto2_port/0.8.0/usb'.
0.003396 gphoto2-port-info-list(2): Loaded 'Universal Serial Bus' ('usb:001,015') from '/usr/lib/libgphoto2_port/0.8.0/usb'.
0.003406 gphoto2-port-info-list(2): Loaded 'Universal Serial Bus' ('usb:001,008') from '/usr/lib/libgphoto2_port/0.8.0/usb'.
0.003416 gphoto2-port-info-list(2): Loaded 'Universal Serial Bus' ('usb:001,006') from '/usr/lib/libgphoto2_port/0.8.0/usb'.
0.003435 gphoto2-port-info-list(2): Counting entries (14 available)...
0.003445 gphoto2-port-info-list(2): 10 regular entries available.
0.005426 gphoto2-abilities-list(2): Using ltdl to load camera libraries from '/usr/lib/libgphoto2/2.4.8'...
0.007469 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/adc65'.
0.007484 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/agfa_cl20'.
0.007489 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/aox'.
0.007492 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/barbie'.
0.007496 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/canon'.
0.007504 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/casio_qv'.
0.007507 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/clicksmart310'.
0.007511 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/digigr8'.
0.007516 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/digita'.
0.007520 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/dimagev'.
0.007524 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/dimera3500'.
0.007528 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/directory'.
0.007531 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/enigma13'.
0.007535 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/fuji'.
0.007539 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/gsmart300'.
0.007542 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/hp215'.
0.007546 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/iclick'.
0.007550 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/jamcam'.
0.007553 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/jd11'.
0.007557 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/jl2005a'.
0.007561 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/kodak_dc120'.
0.007565 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/kodak_dc210'.
0.007570 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/kodak_dc240'.
0.007577 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/kodak_dc3200'.
0.007582 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/kodak_ez200'.
0.007585 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/konica'.
0.007589 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/konica_qm150'.
0.007594 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/largan'.
0.007598 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/lg_gsm'.
0.007602 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/mars'.
0.007606 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/mustek'.
0.007609 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/panasonic_coolshot'.
0.007613 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/panasonic_dc1000'.
0.007617 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/panasonic_dc1580'.
0.007621 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/panasonic_l859'.
0.007624 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/pccam300'.
0.007628 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/pccam600'.
0.007632 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/polaroid_pdc320'.
0.007637 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/polaroid_pdc640'.
0.007641 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/polaroid_pdc700'.
0.007645 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/ptp2'.
0.007649 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/ricoh'.
0.007653 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/ricoh_g3'.
0.007658 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/samsung'.
0.007662 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sierra'.
0.007667 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sipix_blink2'.
0.007671 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sipix_web2'.
0.007676 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/smal'.
0.007680 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sonix'.
0.007684 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sony_dscf1'.
0.007689 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sony_dscf55'.
0.007693 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/soundvision'.
0.007697 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/spca50x'.
0.007701 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sq905'.
0.007706 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/stv0674'.
0.007710 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/stv0680'.
0.007714 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sx330z'.
0.007719 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/topfield'.
0.007723 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/toshiba_pdrm11'.
0.007732 gp-abilities-list(2): Found 59 camera drivers.
0.035739 gphoto2-port-info-list(2): Counting entries (14 available)...         
0.035760 gphoto2-port-info-list(2): 10 regular entries available.
0.035766 gphoto2-port(2): Creating new device...
0.035775 gphoto2-port-info-list(2): Getting info of entry 0 (14 available)...
0.035951 gphoto2-port(2): Setting settings...
0.035963 gphoto2-port-info-list(2): Getting info of entry 1 (14 available)...
0.036075 gphoto2-port(2): Setting timeout to 500 millisecond(s)...
0.036083 gphoto2-port(2): Setting settings...
0.036088 gphoto2-port-info-list(2): Getting info of entry 2 (14 available)...
0.036191 gphoto2-port(2): Setting timeout to 500 millisecond(s)...
0.036199 gphoto2-port(2): Setting settings...
0.036203 gphoto2-port-info-list(2): Getting info of entry 3 (14 available)...
0.036308 gphoto2-port(2): Setting timeout to 500 millisecond(s)...
0.036317 gphoto2-port(2): Setting settings...
0.036322 gphoto2-port-info-list(2): Getting info of entry 4 (14 available)...
0.036499 gphoto2-port(2): Setting timeout to 500 millisecond(s)...
0.036512 gphoto2-port(2): Setting settings...
0.036518 gphoto2-port-info-list(2): Getting info of entry 5 (14 available)...
0.037024 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.037034 gphoto2-port(2): Setting settings...
0.037039 libusb(2): gp_port_usb_update(old int=0, conf=-1, alt=-1), (new int=0, conf=-1, alt=-1)
0.037046 gphoto2-abilities-list.c(1): Auto-detecting USB cameras...
0.037067 gphoto2-port-usb(1): Looking for USB device (vendor 0x4a9, product 0x30ee)... found.
0.037073 gphoto2-port-usb(2): inep to look for is 81
0.037078 gphoto2-port-usb(1): Detected defaults: config 1, interface 0, altsetting 0, inep 81, outep 02, intep 83, class ff, subclass ff
0.037085 gphoto2-abilities-list.c(2): Found 'Canon Digital Rebel XT (normal mode)' (0x4a9,0x30ee)
0.037096 gphoto2-port-info-list(2): Getting info of entry 6 (14 available)...
0.037487 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.037496 gphoto2-port(2): Setting settings...
0.037505 libusb(2): gp_port_usb_update(old int=0, conf=-1, alt=-1), (new int=0, conf=-1, alt=-1)
0.037511 gphoto2-abilities-list.c(1): Auto-detecting USB cameras...
0.037787 gphoto2-port-info-list(2): Getting info of entry 7 (14 available)...
0.038217 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.038226 gphoto2-port(2): Setting settings...
0.038231 libusb(2): gp_port_usb_update(old int=0, conf=-1, alt=-1), (new int=0, conf=-1, alt=-1)
0.038237 gphoto2-abilities-list.c(1): Auto-detecting USB cameras...
0.038270 gphoto2-port-usb(1): Looking for USB device (vendor 0x4a9, product 0x30ee)... found.
0.038275 gphoto2-port-usb(2): inep to look for is 81
0.038280 gphoto2-port-usb(1): Detected defaults: config 1, interface 0, altsetting 0, inep 81, outep 02, intep 83, class ff, subclass ff
0.038285 gphoto2-abilities-list.c(2): Found 'Canon Digital Rebel XT (normal mode)' (0x4a9,0x30ee)
0.038292 gphoto2-port-info-list(2): Getting info of entry 8 (14 available)...
0.038727 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.038736 gphoto2-port(2): Setting settings...
0.038741 libusb(2): gp_port_usb_update(old int=0, conf=-1, alt=-1), (new int=0, conf=-1, alt=-1)
0.038747 gphoto2-abilities-list.c(1): Auto-detecting USB cameras...
0.039075 gphoto2-port-info-list(2): Getting info of entry 9 (14 available)...
0.039505 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.039514 gphoto2-port(2): Setting settings...
0.039519 libusb(2): gp_port_usb_update(old int=0, conf=-1, alt=-1), (new int=0, conf=-1, alt=-1)
0.039525 gphoto2-abilities-list.c(1): Auto-detecting USB cameras...
0.039844 gphoto2-port(2): Freeing port...
0.039852 gphoto2-port(2): Closing port...
0.039880 gphoto2(2): Nothing specified, using first entry of autodetect list.

0.039900 gphoto2-camera(2): Setting abilities ('Canon Digital Rebel XT (normal mode)')...
0.039908 gphoto2-setting(2): Setting key 'model' to value 'Canon Digital Rebel XT (normal mode)' (gphoto2)
0.039916 gphoto2-setting(2): Saving 4 setting(s) to file "/home/john/.gphoto/settings"
0.040048 gphoto2-port-info-list(2): Looking for path 'usb:' (14 entries available)...
0.040060 gphoto2-port-info-list(2): Getting info of entry 5 (14 available)...
0.040067 gphoto2-camera(2): Setting port info for port 'Universal Serial Bus' at 'usb:'...
0.040483 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.040491 gphoto2-port(2): Setting settings...
0.040496 libusb(2): gp_port_usb_update(old int=0, conf=-1, alt=-1), (new int=0, conf=-1, alt=-1)
0.040506 gphoto2-setting(2): Setting key 'port' to value 'usb:' (gphoto2)
0.040512 gphoto2-setting(2): Saving 4 setting(s) to file "/home/john/.gphoto/settings"
0.041117 gphoto2-camera(2): Initializing camera...
0.041131 gphoto2-port-usb(1): Looking for USB device (vendor 0x4a9, product 0x30ee)... found.
0.041139 gphoto2-port-usb(2): inep to look for is 81
0.041144 gphoto2-port-usb(1): Detected defaults: config 1, interface 0, altsetting 0, inep 81, outep 02, intep 83, class ff, subclass ff
0.041149 gphoto2-camera(2): Loading '/usr/lib/libgphoto2/2.4.8/canon'...
0.041268 gphoto2-port(2): Opening USB port...
0.041275 libusb(2): gp_port_usb_open()
0.041301 gphoto2-port(0): Camera is already in use.
0.041331 context(0): An error occurred in the io-library ('Could not lock the device'): Camera is already in use.

*** Error ***              
An error occurred in the io-library ('Could not lock the device'): Camera is already in use.
*** Error (-60: 'Could not lock the device') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt --summary --debug

Please make sure there is sufficient quoting around the arguments.

0.048524 gp-camera(2): Freeing camera...
0.048537 gphoto2-port(2): Freeing port...
0.048543 gphoto2-port(2): Closing port...
0.048562 gphoto2-port(0): Could not release interface 0 (Invalid argument).
0.048602 gphoto2-filesystem(2): resetting filesystem
0.048608 libgphoto2/gphoto2-filesys.c(2): Clearing fscache LRU list...
0.048614 libgphoto2/gphoto2-filesys.c(2): fscache LRU list already empty
0.048618 gphoto2-filesystem(2): Internally deleting all folders from '/'...
0.048624 gphoto2-filesystem(2): Lookup folder '/'...
0.048628 gphoto2-filesystem(2): Found! / is 0x1ea13e0
0.048633 gphoto2-filesystem(2): Recurse delete folder 0x1ea13e0//
john@merage-desktop-01:~$ gphoto2 --summary --debug
0.000053 main(2): ALWAYS INCLUDE THE FOLLOWING LINES WHEN SENDING DEBUG MESSAGES TO THE MAILING LIST:
0.000107 main(2): gphoto2 2.4.5
0.000119 main(2): gphoto2 has been compiled with the following options:
0.000127 main(2):  + gcc (C compiler used)
0.000134 main(2):  + popt (mandatory, for handling command-line parameters)
0.000141 main(2):  + exif (for displaying EXIF information)
0.000149 main(2):  + cdk (for accessing configuration options)
0.000156 main(2):  + aa (for displaying live previews)
0.000163 main(2):  + jpeg (for displaying live previews in JPEG format)
0.000170 main(2):  + readline (for easy navigation in the shell)
0.000182 main(2): libgphoto2 2.4.8
0.000191 main(2): libgphoto2 has been compiled with the following options:
0.000199 main(2):  + gcc (C compiler used)
0.000208 main(2):  + ltdl (for portable loading of camlibs)
0.000215 main(2):  + EXIF (for special handling of EXIF files)
0.000223 main(2): libgphoto2_port 0.8.0
0.000232 main(2): libgphoto2_port has been compiled with the following options:
0.000240 main(2):  + gcc (C compiler used)
0.000247 main(2):  + ltdl (for portable loading of camlibs)
0.000254 main(2):  + USB (libusb, for USB cameras)
0.000261 main(2):  + serial (for serial cameras)
0.000269 main(2):  + no resmgr (serial port access and locking)
0.000276 main(2):  + no baudboy (serial port locking)
0.000283 main(2):  + no ttylock (serial port locking)
0.000290 main(2):  + no lockdev (serial port locking)
0.000298 main(2): CAMLIBS env var not set, using compile-time default instead
0.000305 main(2): IOLIBS env var not set, using compile-time default instead
0.000337 setting/gphoto2-setting.c(2): Creating $HOME/.gphoto
0.000425 setting/gphoto2-setting.c(2): Loading settings from file "/home/john/.gphoto/settings"
0.000646 main(2): The user has not specified both a model and a port. Try to figure them out.
0.000672 gphoto2-port-info-list(2): Using ltdl to load io-drivers from '/usr/lib/libgphoto2_port/0.8.0'...
0.000798 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.8.0/disk'.
0.001143 gphoto2-port/disk(2): found fstab fsname proc
0.001189 gphoto2-port/disk(2): found fstab fsname UUID=99562878-247a-4bca-bfb0-949b7dd6e964
0.001207 gphoto2-port/disk(2): found fstab fsname UUID=a19cd7f4-5917-4bf2-9377-12c4562358ed
0.001255 gphoto2-port/disk(2): found mtab fsname /dev/sda5
0.001273 gphoto2-port/disk(2): found mtab fsname proc
0.001292 gphoto2-port/disk(2): found mtab fsname none
0.001312 gphoto2-port/disk(2): found mtab fsname fusectl
0.001322 gphoto2-port/disk(2): found mtab fsname none
0.001346 gphoto2-port/disk(2): found mtab fsname none
0.001367 gphoto2-port/disk(2): found mtab fsname none
0.001385 gphoto2-port/disk(2): found mtab fsname none
0.001403 gphoto2-port/disk(2): found mtab fsname none
0.001422 gphoto2-port/disk(2): found mtab fsname none
0.001440 gphoto2-port/disk(2): found mtab fsname none
0.001459 gphoto2-port/disk(2): found mtab fsname binfmt_misc
0.001485 gphoto2-port/disk(2): found mtab fsname gvfs-fuse-daemon
0.001496 gphoto2-port/disk(2): found mtab fsname /dev/sdc1
0.001516 gphoto2-port/disk(2): found mtab fsname /dev/sdb1
0.001534 gphoto2-port/disk(2): found mtab fsname /dev/sda1
0.001912 gphoto2-port-info-list(2): Could not load port driver list: 'Unspecified error'.
0.001931 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.8.0/ptpip'.
0.002133 gphoto2-port-info-list(2): Loaded 'PTP/IP Connection' ('ptpip:') from '/usr/lib/libgphoto2_port/0.8.0/ptpip'.
0.002153 gphoto2-port-info-list(2): Loaded '' ('^ptpip') from '/usr/lib/libgphoto2_port/0.8.0/ptpip'.
0.002164 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.8.0/serial'.
0.002461 gphoto2-port-info-list(2): Loaded 'Serial Port 0' ('serial:/dev/ttyS0') from '/usr/lib/libgphoto2_port/0.8.0/serial'.
0.002477 gphoto2-port-info-list(2): Loaded 'Serial Port 1' ('serial:/dev/ttyS1') from '/usr/lib/libgphoto2_port/0.8.0/serial'.
0.002488 gphoto2-port-info-list(2): Loaded 'Serial Port 2' ('serial:/dev/ttyS2') from '/usr/lib/libgphoto2_port/0.8.0/serial'.
0.002498 gphoto2-port-info-list(2): Loaded 'Serial Port 3' ('serial:/dev/ttyS3') from '/usr/lib/libgphoto2_port/0.8.0/serial'.
0.002508 gphoto2-port-info-list(2): Loaded '' ('^serial') from '/usr/lib/libgphoto2_port/0.8.0/serial'.
0.002519 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.8.0/usb'.
0.003348 gphoto2-port-info-list(2): Loaded 'Universal Serial Bus' ('usb:') from '/usr/lib/libgphoto2_port/0.8.0/usb'.
0.003367 gphoto2-port-info-list(2): Loaded '' ('^usb:') from '/usr/lib/libgphoto2_port/0.8.0/usb'.
0.003378 gphoto2-port-info-list(2): Loaded 'Universal Serial Bus' ('usb:002,003') from '/usr/lib/libgphoto2_port/0.8.0/usb'.
0.003388 gphoto2-port-info-list(2): Loaded 'Universal Serial Bus' ('usb:001,015') from '/usr/lib/libgphoto2_port/0.8.0/usb'.
0.003398 gphoto2-port-info-list(2): Loaded 'Universal Serial Bus' ('usb:001,008') from '/usr/lib/libgphoto2_port/0.8.0/usb'.
0.003408 gphoto2-port-info-list(2): Loaded 'Universal Serial Bus' ('usb:001,006') from '/usr/lib/libgphoto2_port/0.8.0/usb'.
0.003427 gphoto2-port-info-list(2): Counting entries (14 available)...
0.003437 gphoto2-port-info-list(2): 10 regular entries available.
0.005418 gphoto2-abilities-list(2): Using ltdl to load camera libraries from '/usr/lib/libgphoto2/2.4.8'...
0.007536 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/adc65'.
0.007548 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/agfa_cl20'.
0.007553 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/aox'.
0.007556 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/barbie'.
0.007560 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/canon'.
0.007564 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/casio_qv'.
0.007568 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/clicksmart310'.
0.007571 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/digigr8'.
0.007576 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/digita'.
0.007580 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/dimagev'.
0.007583 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/dimera3500'.
0.007587 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/directory'.
0.007591 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/enigma13'.
0.007595 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/fuji'.
0.007599 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/gsmart300'.
0.007603 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/hp215'.
0.007607 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/iclick'.
0.007611 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/jamcam'.
0.007614 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/jd11'.
0.007617 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/jl2005a'.
0.007621 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/kodak_dc120'.
0.007624 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/kodak_dc210'.
0.007628 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/kodak_dc240'.
0.007631 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/kodak_dc3200'.
0.007635 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/kodak_ez200'.
0.007638 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/konica'.
0.007642 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/konica_qm150'.
0.007646 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/largan'.
0.007650 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/lg_gsm'.
0.007654 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/mars'.
0.007658 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/mustek'.
0.007663 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/panasonic_coolshot'.
0.007667 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/panasonic_dc1000'.
0.007671 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/panasonic_dc1580'.
0.007675 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/panasonic_l859'.
0.007679 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/pccam300'.
0.007683 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/pccam600'.
0.007687 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/polaroid_pdc320'.
0.007690 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/polaroid_pdc640'.
0.007694 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/polaroid_pdc700'.
0.007698 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/ptp2'.
0.007702 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/ricoh'.
0.007705 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/ricoh_g3'.
0.007709 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/samsung'.
0.007712 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sierra'.
0.007717 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sipix_blink2'.
0.007721 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sipix_web2'.
0.007726 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/smal'.
0.007730 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sonix'.
0.007734 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sony_dscf1'.
0.007738 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sony_dscf55'.
0.007743 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/soundvision'.
0.007747 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/spca50x'.
0.007752 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sq905'.
0.007756 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/stv0674'.
0.007761 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/stv0680'.
0.007765 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/sx330z'.
0.007769 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/topfield'.
0.007774 gphoto2-abilities-list(2): Found '/usr/lib/libgphoto2/2.4.8/toshiba_pdrm11'.
0.007782 gp-abilities-list(2): Found 59 camera drivers.
0.035886 gphoto2-port-info-list(2): Counting entries (14 available)...         
0.035907 gphoto2-port-info-list(2): 10 regular entries available.
0.035913 gphoto2-port(2): Creating new device...
0.035920 gphoto2-port-info-list(2): Getting info of entry 0 (14 available)...
0.036103 gphoto2-port(2): Setting settings...
0.036112 gphoto2-port-info-list(2): Getting info of entry 1 (14 available)...
0.036219 gphoto2-port(2): Setting timeout to 500 millisecond(s)...
0.036228 gphoto2-port(2): Setting settings...
0.036234 gphoto2-port-info-list(2): Getting info of entry 2 (14 available)...
0.036323 gphoto2-port(2): Setting timeout to 500 millisecond(s)...
0.036330 gphoto2-port(2): Setting settings...
0.036334 gphoto2-port-info-list(2): Getting info of entry 3 (14 available)...
0.036422 gphoto2-port(2): Setting timeout to 500 millisecond(s)...
0.036429 gphoto2-port(2): Setting settings...
0.036434 gphoto2-port-info-list(2): Getting info of entry 4 (14 available)...
0.036517 gphoto2-port(2): Setting timeout to 500 millisecond(s)...
0.036524 gphoto2-port(2): Setting settings...
0.036529 gphoto2-port-info-list(2): Getting info of entry 5 (14 available)...
0.037014 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.037022 gphoto2-port(2): Setting settings...
0.037028 libusb(2): gp_port_usb_update(old int=0, conf=-1, alt=-1), (new int=0, conf=-1, alt=-1)
0.037034 gphoto2-abilities-list.c(1): Auto-detecting USB cameras...
0.037054 gphoto2-port-usb(1): Looking for USB device (vendor 0x4a9, product 0x30ee)... found.
0.037060 gphoto2-port-usb(2): inep to look for is 81
0.037065 gphoto2-port-usb(1): Detected defaults: config 1, interface 0, altsetting 0, inep 81, outep 02, intep 83, class ff, subclass ff
0.037071 gphoto2-abilities-list.c(2): Found 'Canon Digital Rebel XT (normal mode)' (0x4a9,0x30ee)
0.037079 gphoto2-port-info-list(2): Getting info of entry 6 (14 available)...
0.037488 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.037497 gphoto2-port(2): Setting settings...
0.037502 libusb(2): gp_port_usb_update(old int=0, conf=-1, alt=-1), (new int=0, conf=-1, alt=-1)
0.037508 gphoto2-abilities-list.c(1): Auto-detecting USB cameras...
0.037764 gphoto2-port-info-list(2): Getting info of entry 7 (14 available)...
0.038172 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.038181 gphoto2-port(2): Setting settings...
0.038186 libusb(2): gp_port_usb_update(old int=0, conf=-1, alt=-1), (new int=0, conf=-1, alt=-1)
0.038191 gphoto2-abilities-list.c(1): Auto-detecting USB cameras...
0.038223 gphoto2-port-usb(1): Looking for USB device (vendor 0x4a9, product 0x30ee)... found.
0.038231 gphoto2-port-usb(2): inep to look for is 81
0.038234 gphoto2-port-usb(1): Detected defaults: config 1, interface 0, altsetting 0, inep 81, outep 02, intep 83, class ff, subclass ff
0.038244 gphoto2-abilities-list.c(2): Found 'Canon Digital Rebel XT (normal mode)' (0x4a9,0x30ee)
0.038255 gphoto2-port-info-list(2): Getting info of entry 8 (14 available)...
0.038679 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.038687 gphoto2-port(2): Setting settings...
0.038692 libusb(2): gp_port_usb_update(old int=0, conf=-1, alt=-1), (new int=0, conf=-1, alt=-1)
0.038698 gphoto2-abilities-list.c(1): Auto-detecting USB cameras...
0.039034 gphoto2-port-info-list(2): Getting info of entry 9 (14 available)...
0.039481 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.039490 gphoto2-port(2): Setting settings...
0.039496 libusb(2): gp_port_usb_update(old int=0, conf=-1, alt=-1), (new int=0, conf=-1, alt=-1)
0.039502 gphoto2-abilities-list.c(1): Auto-detecting USB cameras...
0.039817 gphoto2-port(2): Freeing port...
0.039825 gphoto2-port(2): Closing port...
0.039858 gphoto2(2): Nothing specified, using first entry of autodetect list.

0.039879 gphoto2-camera(2): Setting abilities ('Canon Digital Rebel XT (normal mode)')...
0.039887 gphoto2-setting(2): Setting key 'model' to value 'Canon Digital Rebel XT (normal mode)' (gphoto2)
0.039894 gphoto2-setting(2): Saving 4 setting(s) to file "/home/john/.gphoto/settings"
0.040030 gphoto2-port-info-list(2): Looking for path 'usb:' (14 entries available)...
0.040041 gphoto2-port-info-list(2): Getting info of entry 5 (14 available)...
0.040051 gphoto2-camera(2): Setting port info for port 'Universal Serial Bus' at 'usb:'...
0.040459 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.040468 gphoto2-port(2): Setting settings...
0.040473 libusb(2): gp_port_usb_update(old int=0, conf=-1, alt=-1), (new int=0, conf=-1, alt=-1)
0.040479 gphoto2-setting(2): Setting key 'port' to value 'usb:' (gphoto2)
0.040486 gphoto2-setting(2): Saving 4 setting(s) to file "/home/john/.gphoto/settings"
0.040937 gphoto2-camera(2): Initializing camera...
0.040951 gphoto2-port-usb(1): Looking for USB device (vendor 0x4a9, product 0x30ee)... found.
0.040955 gphoto2-port-usb(2): inep to look for is 81
0.040958 gphoto2-port-usb(1): Detected defaults: config 1, interface 0, altsetting 0, inep 81, outep 02, intep 83, class ff, subclass ff
0.040962 gphoto2-camera(2): Loading '/usr/lib/libgphoto2/2.4.8/canon'...
0.041070 gphoto2-port(2): Opening USB port...
0.041076 libusb(2): gp_port_usb_open()
0.041102 libusb(2): claiming interface 0
0.041122 canon/canon/library.c(2): canon camera_init()
0.041135 canon/canon/library.c(2): GPhoto tells us that we should use a USB link.
0.041143 canon/canon/usb.c(2): Initializing the (USB) camera.
0.041152 canon/canon/usb.c(2): canon_usb_camera_init()
0.041159 canon/canon/usb.c(2): canon_usb_identify: USB ID match 0x04a9:0x30ee (model name "Canon:EOS 350D (normal mode)")
0.041169 context(2): Detected a 'Canon:EOS 350D (normal mode)'.
Detected a 'Canon:EOS 350D (normal mode)'.
0.048251 gphoto2-port(2): Reading message (request=0xc value=0x55 index=0x0 size=1=0x1)...
5.047116 context(0): Could not establish initial contact with camera

*** Error ***              
Could not establish initial contact with camera
5.047165 gphoto2-port(2): Closing port...
*** Error (-102: 'Corrupted data') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt --summary --debug

Please make sure there is sufficient quoting around the arguments.

5.047805 gp-camera(2): Freeing camera...
5.047821 gphoto2-port(2): Freeing port...
5.047831 gphoto2-port(2): Closing port...
5.047916 gphoto2-filesystem(2): resetting filesystem
5.047928 libgphoto2/gphoto2-filesys.c(2): Clearing fscache LRU list...
5.047938 libgphoto2/gphoto2-filesys.c(2): fscache LRU list already empty
5.047945 gphoto2-filesystem(2): Internally deleting all folders from '/'...
5.047954 gphoto2-filesystem(2): Lookup folder '/'...
5.047962 gphoto2-filesystem(2): Found! / is 0x9173e0
5.047970 gphoto2-filesystem(2): Recurse delete folder 0x9173e0//

---

