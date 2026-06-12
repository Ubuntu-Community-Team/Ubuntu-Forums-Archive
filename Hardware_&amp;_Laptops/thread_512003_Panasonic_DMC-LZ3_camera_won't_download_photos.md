---
title: "Panasonic DMC-LZ3 camera won't download photos"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by Frem on 2007-07-28
When I plug in this camera (Panasonic DMC-LZ3), and click the button to import photos from it on the dialog box that comes up, the window jams and stops responding.

I tried to import using Fspot, and that gives an error.

I finally used the command "gphoto2 --debug --get-all-files" to see what was going on. This is the output it gave me: 

```
james@james:~$ gphoto2 --debug --get-all-files
0.000335 main(2): ALWAYS INCLUDE THE FOLLOWING LINES WHEN SENDING DEBUG MESSAGES TO THE MAILING LIST:
0.000553 main(2): gphoto2 2.2.0
0.000634 main(2): gphoto2 has been compiled with the following options:
0.000708 main(2):  + gcc (C compiler used)
0.000780 main(2):  + popt (for handling command-line parameters)
0.000852 main(2):  + exif (for displaying EXIF information)
0.000924 main(2):  + cdk (for accessing configuration options)
0.000995 main(2):  + no aa (for displaying live previews)
0.001066 main(2):  + jpeg (for displaying live previews in JPEG format)
0.001138 main(2):  + readline (for easy navigation in the shell)
0.001213 main(2): libgphoto2 2.3.0
0.001289 main(2): libgphoto2 has been compiled with the following options:
0.001362 main(2):  + gcc (C compiler used)
0.001434 main(2):  + no ltdl (for portable loading of camlibs)
0.001505 main(2):  + EXIF (for special handling of EXIF files)
0.001580 main(2): libgphoto2_port 0.7.0
0.001656 main(2): libgphoto2_port has been compiled with the following options:
0.001729 main(2):  + gcc (C compiler used)
0.001800 main(2):  + no ltdl (for portable loading of camlibs)
0.001872 main(2):  + USB (libusb, for USB cameras)
0.001943 main(2):  + serial (for serial cameras)
0.002014 main(2):  + no resmgr (serial port access and locking)
0.002086 main(2):  + no baudboy (serial port locking)
0.002158 main(2):  + no ttylock (serial port locking)
0.002229 main(2):  + no lockdev (serial port locking)
0.002383 main(2): The user has not specified both a model and a port. Try to figure them out.
0.002485 gphoto2-port-info-list(2): Using ltdl to load io-drivers from '/usr/lib/libgphoto2_port/0.7.0'...
0.002692 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.7.0/disk'.
0.005740 gphoto2-port/disk(2): found 4 volumes
0.011723 gphoto2-port-info-list(2): Loaded 'Media 'Volume (vfat)'' ('disk:/media/transfer') from '/usr/lib/libgphoto2_port/0.7.0/disk'.
0.015710 gphoto2-port-info-list(2): Loaded 'Media 'Volume (ext3)'' ('disk:/') from '/usr/lib/libgphoto2_port/0.7.0/disk'.
0.015918 gphoto2-port-info-list(2): Loaded 'Media 'Windows'' ('disk:/media/windows') from '/usr/lib/libgphoto2_port/0.7.0/disk'.
0.015995 gphoto2-port-info-list(2): Loaded '' ('^disk:') from '/usr/lib/libgphoto2_port/0.7.0/disk'.
0.016074 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.7.0/ptpip'.
0.016397 gphoto2-port-info-list(2): Loaded 'PTP/IP Connection' ('ptpip:') from '/usr/lib/libgphoto2_port/0.7.0/ptpip'.
0.016487 gphoto2-port-info-list(2): Loaded '' ('^ptpip') from '/usr/lib/libgphoto2_port/0.7.0/ptpip'.
0.016565 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.016742 gphoto2-port-serial(2): Trying to lock '/dev/ttyS0'...
0.016890 gphoto2-port-serial(2): Trying to lock '/dev/ttyS1'...
0.016991 gphoto2-port-serial(2): Trying to lock '/dev/ttyS2'...
0.017089 gphoto2-port-serial(2): Trying to lock '/dev/ttyS3'...
0.017273 gphoto2-port-info-list(2): Loaded 'Serial Port 0' ('serial:/dev/ttyS0') from '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.017355 gphoto2-port-info-list(2): Loaded 'Serial Port 1' ('serial:/dev/ttyS1') from '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.017431 gphoto2-port-info-list(2): Loaded 'Serial Port 2' ('serial:/dev/ttyS2') from '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.017507 gphoto2-port-info-list(2): Loaded 'Serial Port 3' ('serial:/dev/ttyS3') from '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.017583 gphoto2-port-info-list(2): Loaded '' ('^serial') from '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.017660 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.7.0/usb'.
0.264086 gphoto2-port-info-list(2): Loaded 'Universal Serial Bus' ('usb:') from '/usr/lib/libgphoto2_port/0.7.0/usb'.
0.264238 gphoto2-port-info-list(2): Loaded '' ('^usb:') from '/usr/lib/libgphoto2_port/0.7.0/usb'.
0.264584 gphoto2-port-info-list(2): Counting entries (13 available)...
0.264682 gphoto2-port-info-list(2): 9 regular entries available.
0.264759 gphoto2-port(2): Creating new device...
0.264843 gphoto2-port-info-list(2): Getting info of entry 0 (13 available)...
0.265274 gphoto2-port(2): Setting settings...
0.265385 gphoto2-port(0): The operation 'update' is not supported by this device
0.265484 gphoto2-port-info-list(2): Getting info of entry 1 (13 available)...
0.265773 gphoto2-port(2): Setting settings...
0.265865 gphoto2-port(0): The operation 'update' is not supported by this device
0.265946 gphoto2-port-info-list(2): Getting info of entry 2 (13 available)...
0.266211 gphoto2-port(2): Setting settings...
0.266301 gphoto2-port(0): The operation 'update' is not supported by this device
0.266385 gphoto2-port-info-list(2): Getting info of entry 3 (13 available)...
0.266562 gphoto2-port(2): Setting settings...
0.266647 gphoto2-port-info-list(2): Getting info of entry 4 (13 available)...
0.266816 gphoto2-port(2): Setting timeout to 500 millisecond(s)...
0.266899 gphoto2-port(2): Setting settings...
0.266979 gphoto2-port-info-list(2): Getting info of entry 5 (13 available)...
0.267133 gphoto2-port(2): Setting timeout to 500 millisecond(s)...
0.267215 gphoto2-port(2): Setting settings...
0.267293 gphoto2-port-info-list(2): Getting info of entry 6 (13 available)...
0.267442 gphoto2-port(2): Setting timeout to 500 millisecond(s)...
0.267524 gphoto2-port(2): Setting settings...
0.267602 gphoto2-port-info-list(2): Getting info of entry 7 (13 available)...
0.267752 gphoto2-port(2): Setting timeout to 500 millisecond(s)...
0.267989 gphoto2-port(2): Setting settings...
0.268068 gphoto2-port-info-list(2): Getting info of entry 8 (13 available)...
0.268616 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.268719 gphoto2-port(2): Setting settings...
0.268794 gphoto2-abilities-list.c(1): Auto-detecting USB cameras...
0.268887 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.268971 gphoto2-port(0): Could not find USB device (vendor 0x6bd, product 0x403). Make sure this device is connected to the computer.
0.269051 gphoto2-port(0): Could not find USB device (vendor 0x6bd, product 0x404). Make sure this device is connected to the computer.
0.269132 gphoto2-port(0): Could not find USB device (vendor 0x4fc, product 0x504b). Make sure this device is connected to the computer.
0.269212 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.269293 gphoto2-port(0): Could not find USB device (vendor 0x4fc, product 0x504a). Make sure this device is connected to the computer.
0.269373 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.269453 gphoto2-port(0): Could not find USB device (vendor 0x8ca, product 0x111). Make sure this device is connected to the computer.
0.269533 gphoto2-port(0): Could not find USB device (vendor 0x4fc, product 0x504a). Make sure this device is connected to the computer.
0.269613 gphoto2-port(0): Could not find USB device (vendor 0x4fc, product 0x504b). Make sure this device is connected to the computer.
0.269694 gphoto2-port(0): Could not find USB device (vendor 0xe79, product 0x120a). Make sure this device is connected to the computer.
0.269773 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.269853 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.269933 gphoto2-port(0): Could not find USB device (vendor 0x93a, product 0x10f). Make sure this device is connected to the computer.
0.270013 gphoto2-port(0): Could not find USB device (vendor 0x93a, product 0x10f). Make sure this device is connected to the computer.
0.270093 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x913c). Make sure this device is connected to the computer.
0.270172 gphoto2-port(0): Could not find USB device (vendor 0x919, product 0x100). Make sure this device is connected to the computer.
0.270252 gphoto2-port(0): Could not find USB device (vendor 0x93a, product 0x10f). Make sure this device is connected to the computer.
0.270332 gphoto2-port(0): Could not find USB device (vendor 0x4a5, product 0x3003). Make sure this device is connected to the computer.
0.270411 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3047). Make sure this device is connected to the computer.
0.270491 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30c0). Make sure this device is connected to the computer.
0.270571 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x304d). Make sure this device is connected to the computer.
0.270650 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3066). Make sure this device is connected to the computer.
0.270730 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30bf). Make sure this device is connected to the computer.
0.270809 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3075). Make sure this device is connected to the computer.
0.270889 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3075). Make sure this device is connected to the computer.
0.270969 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30ba). Make sure this device is connected to the computer.
0.271048 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30ba). Make sure this device is connected to the computer.
0.271127 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30c1). Make sure this device is connected to the computer.
0.271207 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x310e). Make sure this device is connected to the computer.
0.271286 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b4). Make sure this device is connected to the computer.
0.271366 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b4). Make sure this device is connected to the computer.
0.271446 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30ff). Make sure this device is connected to the computer.
0.271526 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x311c). Make sure this device is connected to the computer.
0.271605 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30fe). Make sure this device is connected to the computer.
0.271685 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30f2). Make sure this device is connected to the computer.
0.271765 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3116). Make sure this device is connected to the computer.
0.271968 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3119). Make sure this device is connected to the computer.
0.272049 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3136). Make sure this device is connected to the computer.
0.272128 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x309b). Make sure this device is connected to the computer.
0.272208 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x309b). Make sure this device is connected to the computer.
0.272287 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30c4). Make sure this device is connected to the computer.
0.272366 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3072). Make sure this device is connected to the computer.
0.272446 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3072). Make sure this device is connected to the computer.
0.272525 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b6). Make sure this device is connected to the computer.
0.272605 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b6). Make sure this device is connected to the computer.
0.272684 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3052). Make sure this device is connected to the computer.
0.272764 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3065). Make sure this device is connected to the computer.
0.272843 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3070). Make sure this device is connected to the computer.
0.272922 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3071). Make sure this device is connected to the computer.
0.273001 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30f1). Make sure this device is connected to the computer.
0.273081 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x306a). Make sure this device is connected to the computer.
0.273160 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3088). Make sure this device is connected to the computer.
0.278599 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3087). Make sure this device is connected to the computer.
0.278684 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3083). Make sure this device is connected to the computer.
0.278764 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30ea). Make sure this device is connected to the computer.
0.278845 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30ec). Make sure this device is connected to the computer.
0.278925 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3084). Make sure this device is connected to the computer.
0.279005 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3099). Make sure this device is connected to the computer.
0.279085 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3113). Make sure this device is connected to the computer.
0.279165 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30ef). Make sure this device is connected to the computer.
0.279244 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30ee). Make sure this device is connected to the computer.
0.279324 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3110). Make sure this device is connected to the computer.
0.279404 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3101). Make sure this device is connected to the computer.
0.279484 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3044). Make sure this device is connected to the computer.
0.279563 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3060). Make sure this device is connected to the computer.
0.279644 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3084). Make sure this device is connected to the computer.
0.279723 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3099). Make sure this device is connected to the computer.
0.279937 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3084). Make sure this device is connected to the computer.
0.280018 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3099). Make sure this device is connected to the computer.
0.280098 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x308e). Make sure this device is connected to the computer.
0.280178 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3046). Make sure this device is connected to the computer.
0.280258 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x304b). Make sure this device is connected to the computer.
0.280338 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30ba). Make sure this device is connected to the computer.
0.280417 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b4). Make sure this device is connected to the computer.
0.280497 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30c1). Make sure this device is connected to the computer.
0.280577 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30c4). Make sure this device is connected to the computer.
0.280657 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x306b). Make sure this device is connected to the computer.
0.280737 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3096). Make sure this device is connected to the computer.
0.280816 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x307c). Make sure this device is connected to the computer.
0.280896 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x307a). Make sure this device is connected to the computer.
0.280976 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3096). Make sure this device is connected to the computer.
0.281056 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x308e). Make sure this device is connected to the computer.
0.281136 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3082). Make sure this device is connected to the computer.
0.281215 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3081). Make sure this device is connected to the computer.
0.281295 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3080). Make sure this device is connected to the computer.
0.281375 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30a9). Make sure this device is connected to the computer.
0.281455 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x306b). Make sure this device is connected to the computer.
0.281534 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3082). Make sure this device is connected to the computer.
0.281615 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3081). Make sure this device is connected to the computer.
0.281695 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x307f). Make sure this device is connected to the computer.
0.281775 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3080). Make sure this device is connected to the computer.
0.281854 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x306b). Make sure this device is connected to the computer.
0.281934 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3096). Make sure this device is connected to the computer.
0.282014 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30a9). Make sure this device is connected to the computer.
0.282093 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3105). Make sure this device is connected to the computer.
0.282173 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x308e). Make sure this device is connected to the computer.
0.282253 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x304f). Make sure this device is connected to the computer.
0.282333 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3061). Make sure this device is connected to the computer.
0.282412 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x304e). Make sure this device is connected to the computer.
0.282492 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3062). Make sure this device is connected to the computer.
0.282572 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3059). Make sure this device is connected to the computer.
0.282652 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3076). Make sure this device is connected to the computer.
0.282731 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3076). Make sure this device is connected to the computer.
0.282811 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b8). Make sure this device is connected to the computer.
0.282891 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b8). Make sure this device is connected to the computer.
0.282971 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3058). Make sure this device is connected to the computer.
0.283051 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b7). Make sure this device is connected to the computer.
0.283131 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b7). Make sure this device is connected to the computer.
0.283210 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30f9). Make sure this device is connected to the computer.
0.283290 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30f8). Make sure this device is connected to the computer.
0.283370 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30c2). Make sure this device is connected to the computer.
0.283450 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30c2). Make sure this device is connected to the computer.
0.283530 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30c1). Make sure this device is connected to the computer.
0.283610 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3126). Make sure this device is connected to the computer.
0.283689 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x311b). Make sure this device is connected to the computer.
0.283990 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3074). Make sure this device is connected to the computer.
0.284073 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3074). Make sure this device is connected to the computer.
0.284152 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30fd). Make sure this device is connected to the computer.
0.284232 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30fc). Make sure this device is connected to the computer.
0.284312 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x313a). Make sure this device is connected to the computer.
0.284391 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3139). Make sure this device is connected to the computer.
0.284471 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3073). Make sure this device is connected to the computer.
0.284551 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3073). Make sure this device is connected to the computer.
0.284631 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3117). Make sure this device is connected to the computer.
0.284711 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3138). Make sure this device is connected to the computer.
0.284791 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b5). Make sure this device is connected to the computer.
0.284870 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b5). Make sure this device is connected to the computer.
0.284950 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x309a). Make sure this device is connected to the computer.
0.285029 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x309a). Make sure this device is connected to the computer.
0.285108 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b9). Make sure this device is connected to the computer.
0.285188 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b9). Make sure this device is connected to the computer.
0.285267 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30bb). Make sure this device is connected to the computer.
0.285346 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30bb). Make sure this device is connected to the computer.
0.285426 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3048). Make sure this device is connected to the computer.
0.285505 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3055). Make sure this device is connected to the computer.
0.285584 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x306e). Make sure this device is connected to the computer.
0.285664 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x306f). Make sure this device is connected to the computer.
0.285744 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3085). Make sure this device is connected to the computer.
0.285823 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3085). Make sure this device is connected to the computer.
0.285903 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b3). Make sure this device is connected to the computer.
0.285982 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b3). Make sure this device is connected to the computer.
0.286062 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3125). Make sure this device is connected to the computer.
0.286141 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x309b). Make sure this device is connected to the computer.
0.286221 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3049). Make sure this device is connected to the computer.
0.286301 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x309c). Make sure this device is connected to the computer.
0.286380 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3041). Make sure this device is connected to the computer.
0.286460 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3045). Make sure this device is connected to the computer.
0.286539 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3051). Make sure this device is connected to the computer.
0.286619 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30f0). Make sure this device is connected to the computer.
0.286699 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3043). Make sure this device is connected to the computer.
0.286778 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3065). Make sure this device is connected to the computer.
0.286857 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3070). Make sure this device is connected to the computer.
0.286937 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3071). Make sure this device is connected to the computer.
0.287017 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x311a). Make sure this device is connected to the computer.
0.287096 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3057). Make sure this device is connected to the computer.
0.287176 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x304c). Make sure this device is connected to the computer.
0.287256 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3066). Make sure this device is connected to the computer.
0.287354 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3056). Make sure this device is connected to the computer.
0.287434 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3075). Make sure this device is connected to the computer.
0.287514 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30ba). Make sure this device is connected to the computer.
0.287594 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30ba). Make sure this device is connected to the computer.
0.300389 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x306c). Make sure this device is connected to the computer.
0.300481 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x306d). Make sure this device is connected to the computer.
0.300562 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3077). Make sure this device is connected to the computer.
0.300642 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3077). Make sure this device is connected to the computer.
0.300722 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b4). Make sure this device is connected to the computer.
0.300802 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b4). Make sure this device is connected to the computer.
0.300883 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b2). Make sure this device is connected to the computer.
0.300963 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b2). Make sure this device is connected to the computer.
0.301042 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b1). Make sure this device is connected to the computer.
0.301122 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b1). Make sure this device is connected to the computer.
0.301202 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30fa). Make sure this device is connected to the computer.
0.301283 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x309b). Make sure this device is connected to the computer.
0.301363 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3072). Make sure this device is connected to the computer.
0.301443 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3072). Make sure this device is connected to the computer.
0.301522 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b6). Make sure this device is connected to the computer.
0.301602 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30b6). Make sure this device is connected to the computer.
0.301682 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30c4). Make sure this device is connected to the computer.
0.301761 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30c0). Make sure this device is connected to the computer.
0.301841 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30c1). Make sure this device is connected to the computer.
0.301921 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30f1). Make sure this device is connected to the computer.
0.302000 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30ff). Make sure this device is connected to the computer.
0.302080 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30f2). Make sure this device is connected to the computer.
0.302160 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x311c). Make sure this device is connected to the computer.
0.302239 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x30fe). Make sure this device is connected to the computer.
0.302319 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3119). Make sure this device is connected to the computer.
0.302399 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3050). Make sure this device is connected to the computer.
0.302479 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x305c). Make sure this device is connected to the computer.
0.302559 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3078). Make sure this device is connected to the computer.
0.302638 gphoto2-port(0): Could not find USB device (vendor 0x7cf, product 0x1042). Make sure this device is connected to the computer.
0.302719 gphoto2-port(0): Could not find USB device (vendor 0x55f, product 0xc200). Make sure this device is connected to the computer.
0.302799 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.302879 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x905c). Make sure this device is connected to the computer.
0.302958 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.303038 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x1002). Make sure this device is connected to the computer.
0.303118 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.303198 gphoto2-port(0): Could not find USB device (vendor 0x797, product 0x8001). Make sure this device is connected to the computer.
0.303278 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.303357 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.303437 gphoto2-port(0): Could not find USB device (vendor 0xd96, product 0x4100). Make sure this device is connected to the computer.
0.303516 gphoto2-port(0): Could not find USB device (vendor 0x3e8, product 0x2182). Make sure this device is connected to the computer.
0.303595 gphoto2-port(0): Could not find USB device (vendor 0x3e8, product 0x2180). Make sure this device is connected to the computer.
0.303675 gphoto2-port(0): Could not find USB device (vendor 0x919, product 0x100). Make sure this device is connected to the computer.
0.303755 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4007). Make sure this device is connected to the computer.
0.304038 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x400a). Make sure this device is connected to the computer.
0.304119 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4012). Make sure this device is connected to the computer.
0.304198 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x400b). Make sure this device is connected to the computer.
0.304278 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4013). Make sure this device is connected to the computer.
0.304357 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4123). Make sure this device is connected to the computer.
0.304437 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4130). Make sure this device is connected to the computer.
0.304517 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x413c). Make sure this device is connected to the computer.
0.304597 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4137). Make sure this device is connected to the computer.
0.304676 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x413d). Make sure this device is connected to the computer.
0.304757 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4131). Make sure this device is connected to the computer.
0.304838 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4150). Make sure this device is connected to the computer.
0.304918 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4152). Make sure this device is connected to the computer.
0.304997 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x411f). Make sure this device is connected to the computer.
0.305077 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4151). Make sure this device is connected to the computer.
0.305157 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4153). Make sure this device is connected to the computer.
0.305237 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x413e). Make sure this device is connected to the computer.
0.305316 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4128). Make sure this device is connected to the computer.
0.305396 gphoto2-port(0): Could not find USB device (vendor 0x84d, product 0x3). Make sure this device is connected to the computer.
0.305476 gphoto2-port(0): Could not find USB device (vendor 0xd64, product 0x1021). Make sure this device is connected to the computer.
0.305556 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x905c). Make sure this device is connected to the computer.
0.305636 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.305715 gphoto2-port(0): Could not find USB device (vendor 0xc45, product 0x8000). Make sure this device is connected to the computer.
0.305794 gphoto2-port(0): Could not find USB device (vendor 0x413c, product 0x4500). Make sure this device is connected to the computer.
0.305874 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4132). Make sure this device is connected to the computer.
0.305953 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x905c). Make sure this device is connected to the computer.
0.306032 gphoto2-port(0): Could not find USB device (vendor 0x93a, product 0x10e). Make sure this device is connected to the computer.
0.306112 gphoto2-port(0): Could not find USB device (vendor 0x5da, product 0x1018). Make sure this device is connected to the computer.
0.306193 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.306273 gphoto2-port(0): Could not find USB device (vendor 0x919, product 0x100). Make sure this device is connected to the computer.
0.306353 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.306433 gphoto2-port(0): Could not find USB device (vendor 0x1183, product 0x1). Make sure this device is connected to the computer.
0.306512 gphoto2-port(0): Could not find USB device (vendor 0x5da, product 0x1020). Make sure this device is connected to the computer.
0.306592 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.306672 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.306752 gphoto2-port(0): Could not find USB device (vendor 0x10d6, product 0x2200). Make sure this device is connected to the computer.
0.306831 gphoto2-port(0): Could not find USB device (vendor 0x10d6, product 0x2200). Make sure this device is connected to the computer.
0.306912 gphoto2-port(0): Could not find USB device (vendor 0x93a, product 0x10e). Make sure this device is connected to the computer.
0.306991 gphoto2-port(0): Could not find USB device (vendor 0x93a, product 0x10f). Make sure this device is connected to the computer.
0.307071 gphoto2-port(0): Could not find USB device (vendor 0x4b8, product 0x403). Make sure this device is connected to the computer.
0.307152 gphoto2-port(0): Could not find USB device (vendor 0x4b8, product 0x402). Make sure this device is connected to the computer.
0.307232 gphoto2-port(0): Could not find USB device (vendor 0xdca, product 0x2). Make sure this device is connected to the computer.
0.307311 gphoto2-port(0): Could not find USB device (vendor 0xdca, product 0x2). Make sure this device is connected to the computer.
0.307392 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x14a). Make sure this device is connected to the computer.
0.307471 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x193). Make sure this device is connected to the computer.
0.307551 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x19b). Make sure this device is connected to the computer.
0.307630 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x142). Make sure this device is connected to the computer.
0.307710 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.308140 gphoto2-port(0): Could not find USB device (vendor 0x919, product 0x100). Make sure this device is connected to the computer.
0.308226 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.308306 gphoto2-port(0): Could not find USB device (vendor 0x919, product 0x100). Make sure this device is connected to the computer.
0.308386 gphoto2-port(0): Could not find USB device (vendor 0x797, product 0x801c). Make sure this device is connected to the computer.
0.308465 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.308545 gphoto2-port(0): Could not find USB device (vendor 0x93a, product 0x10e). Make sure this device is connected to the computer.
0.308625 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.308706 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6502). Make sure this device is connected to the computer.
0.308785 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6202). Make sure this device is connected to the computer.
0.308865 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7c02). Make sure this device is connected to the computer.
0.308945 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7d02). Make sure this device is connected to the computer.
0.309025 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6302). Make sure this device is connected to the computer.
0.309105 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6602). Make sure this device is connected to the computer.
0.309185 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7402). Make sure this device is connected to the computer.
0.309264 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7802). Make sure this device is connected to the computer.
0.309345 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7202). Make sure this device is connected to the computer.
0.309425 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6e02). Make sure this device is connected to the computer.
0.309504 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7902). Make sure this device is connected to the computer.
0.309584 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6d02). Make sure this device is connected to the computer.
0.309663 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6302). Make sure this device is connected to the computer.
0.309743 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x4102). Make sure this device is connected to the computer.
0.309823 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6802). Make sure this device is connected to the computer.
0.309902 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7102). Make sure this device is connected to the computer.
0.309982 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6b02). Make sure this device is connected to the computer.
0.310062 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6402). Make sure this device is connected to the computer.
0.310141 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7602). Make sure this device is connected to the computer.
0.310221 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6702). Make sure this device is connected to the computer.
0.310300 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6c02). Make sure this device is connected to the computer.
0.310379 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6a02). Make sure this device is connected to the computer.
0.310459 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x4202). Make sure this device is connected to the computer.
0.310538 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7702). Make sure this device is connected to the computer.
0.310617 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7e02). Make sure this device is connected to the computer.
0.310697 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x4302). Make sure this device is connected to the computer.
0.310776 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x4102). Make sure this device is connected to the computer.
0.310856 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x4402). Make sure this device is connected to the computer.
0.310936 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x4502). Make sure this device is connected to the computer.
0.311016 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x4102). Make sure this device is connected to the computer.
0.311095 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6002). Make sure this device is connected to the computer.
0.311175 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8b02). Make sure this device is connected to the computer.
0.311255 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7502). Make sure this device is connected to the computer.
0.311335 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7b02). Make sure this device is connected to the computer.
0.311415 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7302). Make sure this device is connected to the computer.
0.311494 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7a02). Make sure this device is connected to the computer.
0.311574 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8002). Make sure this device is connected to the computer.
0.311653 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8102). Make sure this device is connected to the computer.
0.311733 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8202). Make sure this device is connected to the computer.
0.311903 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8402). Make sure this device is connected to the computer.
0.311982 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8502). Make sure this device is connected to the computer.
0.312062 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8702). Make sure this device is connected to the computer.
0.312141 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9153). Make sure this device is connected to the computer.
0.312221 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.312301 gphoto2-port(0): Could not find USB device (vendor 0x93a, product 0x10e). Make sure this device is connected to the computer.
0.312381 gphoto2-port(0): Could not find USB device (vendor 0x45e, product 0xc9). Make sure this device is connected to the computer.
0.312461 gphoto2-port(0): Could not find USB device (vendor 0x8086, product 0x630). Make sure this device is connected to the computer.
0.312540 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.312620 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x112a). Make sure this device is connected to the computer.
0.312699 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x2102). Make sure this device is connected to the computer.
0.312779 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x2101). Make sure this device is connected to the computer.
0.312858 gphoto2-port(0): Could not find USB device (vendor 0x1006, product 0x4003). Make sure this device is connected to the computer.
0.312938 gphoto2-port(0): Could not find USB device (vendor 0x1006, product 0x4002). Make sure this device is connected to the computer.
0.313017 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1117). Make sure this device is connected to the computer.
0.313097 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1113). Make sure this device is connected to the computer.
0.313177 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1120). Make sure this device is connected to the computer.
0.313256 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1118). Make sure this device is connected to the computer.
0.313336 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1114). Make sure this device is connected to the computer.
0.313416 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1119). Make sure this device is connected to the computer.
0.313495 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1116). Make sure this device is connected to the computer.
0.313575 gphoto2-port(0): Could not find USB device (vendor 0x784, product 0x100). Make sure this device is connected to the computer.
0.313678 gphoto2-port(0): Could not find USB device (vendor 0xd96, product 0x3300). Make sure this device is connected to the computer.
0.313758 gphoto2-port(0): Could not find USB device (vendor 0xd96, product 0x4100). Make sure this device is connected to the computer.
0.313838 gphoto2-port(0): Could not find USB device (vendor 0x5da, product 0x1006). Make sure this device is connected to the computer.
0.313918 gphoto2-port(0): Could not find USB device (vendor 0xd96, product 0x0). Make sure this device is connected to the computer.
0.313998 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.314078 gphoto2-port(0): Could not find USB device (vendor 0x4f1, product 0x6105). Make sure this device is connected to the computer.
0.314158 gphoto2-port(0): Could not find USB device (vendor 0x84e, product 0x1). Make sure this device is connected to the computer.
0.314237 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x57e). Make sure this device is connected to the computer.
0.314317 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x58a). Make sure this device is connected to the computer.
0.314396 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x58c). Make sure this device is connected to the computer.
0.314475 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x58d). Make sure this device is connected to the computer.
0.314555 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x589). Make sure this device is connected to the computer.
0.314634 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x59a). Make sure this device is connected to the computer.
0.314714 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x5a2). Make sure this device is connected to the computer.
0.314793 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x5ba). Make sure this device is connected to the computer.
0.314873 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x5a7). Make sure this device is connected to the computer.
0.314953 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x59c). Make sure this device is connected to the computer.
0.315033 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x560). Make sure this device is connected to the computer.
0.315112 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x560). Make sure this device is connected to the computer.
0.315192 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x535). Make sure this device is connected to the computer.
0.315272 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x566). Make sure this device is connected to the computer.
0.315352 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x566). Make sure this device is connected to the computer.
0.315432 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x574). Make sure this device is connected to the computer.
0.315511 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x573). Make sure this device is connected to the computer.
0.315592 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x571). Make sure this device is connected to the computer.
0.315672 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x584). Make sure this device is connected to the computer.
0.315752 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x579). Make sure this device is connected to the computer.
0.315927 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x578). Make sure this device is connected to the computer.
0.316006 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x578). Make sure this device is connected to the computer.
0.316086 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x57a). Make sure this device is connected to the computer.
0.316166 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x57b). Make sure this device is connected to the computer.
0.316245 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x586). Make sure this device is connected to the computer.
0.316325 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x57c). Make sure this device is connected to the computer.
0.316405 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x100). Make sure this device is connected to the computer.
0.316485 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x120). Make sure this device is connected to the computer.
0.316565 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x121). Make sure this device is connected to the computer.
0.316644 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x110). Make sure this device is connected to the computer.
0.316724 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x111). Make sure this device is connected to the computer.
0.316804 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x130). Make sure this device is connected to the computer.
0.316884 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x112). Make sure this device is connected to the computer.
0.316963 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x132). Make sure this device is connected to the computer.
0.317043 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x160). Make sure this device is connected to the computer.
0.317122 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x131). Make sure this device is connected to the computer.
0.317202 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x525). Make sure this device is connected to the computer.
0.317281 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x500). Make sure this device is connected to the computer.
0.317361 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x510). Make sure this device is connected to the computer.
0.317440 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x530). Make sure this device is connected to the computer.
0.317519 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x170). Make sure this device is connected to the computer.
0.317598 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x555). Make sure this device is connected to the computer.
0.317678 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x576). Make sure this device is connected to the computer.
0.317757 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x550). Make sure this device is connected to the computer.
0.317837 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x570). Make sure this device is connected to the computer.
0.317923 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x572). Make sure this device is connected to the computer.
0.318003 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x575). Make sure this device is connected to the computer.
0.318083 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x57d). Make sure this device is connected to the computer.
0.318162 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x57f). Make sure this device is connected to the computer.
0.318241 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x577). Make sure this device is connected to the computer.
0.318320 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x300). Make sure this device is connected to the computer.
0.318399 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x540). Make sure this device is connected to the computer.
0.318478 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x568). Make sure this device is connected to the computer.
0.318558 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x569). Make sure this device is connected to the computer.
0.318637 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x565). Make sure this device is connected to the computer.
0.318716 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x567). Make sure this device is connected to the computer.
0.318796 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x400). Make sure this device is connected to the computer.
0.318875 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x592). Make sure this device is connected to the computer.
0.318955 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x58e). Make sure this device is connected to the computer.
0.319034 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x58f). Make sure this device is connected to the computer.
0.319120 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x59d). Make sure this device is connected to the computer.
0.319199 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x59e). Make sure this device is connected to the computer.
0.319279 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x587). Make sure this device is connected to the computer.
0.319358 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x580). Make sure this device is connected to the computer.
0.319438 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x588). Make sure this device is connected to the computer.
0.319518 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x403). Make sure this device is connected to the computer.
0.319597 gphoto2-port(0): Could not find USB device (vendor 0x4c8, product 0x722). Make sure this device is connected to the computer.
0.319678 gphoto2-port(0): Could not find USB device (vendor 0x132b, product 0x1). Make sure this device is connected to the computer.
0.319757 gphoto2-port(0): Could not find USB device (vendor 0x132b, product 0x7). Make sure this device is connected to the computer.
0.320088 gphoto2-port(0): Could not find USB device (vendor 0x132b, product 0x18). Make sure this device is connected to the computer.
0.320169 gphoto2-port(0): Could not find USB device (vendor 0x132b, product 0x22). Make sure this device is connected to the computer.
0.320249 gphoto2-port(0): Could not find USB device (vendor 0x4da, product 0x2375). Make sure this device is connected to the computer.
0.320329 gphoto2-port(0): Could not find USB device (vendor 0x1004, product 0x6005). Make sure this device is connected to the computer.
0.320409 gphoto2-port(0): Could not find USB device (vendor 0xd96, product 0x4100). Make sure this device is connected to the computer.
0.320488 gphoto2-port(0): Could not find USB device (vendor 0x46d, product 0x900). Make sure this device is connected to the computer.
0.320568 gphoto2-port(0): Could not find USB device (vendor 0x46d, product 0x950). Make sure this device is connected to the computer.
0.320649 gphoto2-port(0): Could not find USB device (vendor 0xd96, product 0x4100). Make sure this device is connected to the computer.
0.320728 gphoto2-port(0): Could not find USB device (vendor 0xd96, product 0x3300). Make sure this device is connected to the computer.
0.320809 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.320889 gphoto2-port(0): Could not find USB device (vendor 0x4fc, product 0x504b). Make sure this device is connected to the computer.
0.320969 gphoto2-port(0): Could not find USB device (vendor 0x919, product 0x100). Make sure this device is connected to the computer.
0.321048 gphoto2-port(0): Could not find USB device (vendor 0x4fc, product 0x504a). Make sure this device is connected to the computer.
0.321129 gphoto2-port(0): Could not find USB device (vendor 0xd96, product 0x4100). Make sure this device is connected to the computer.
0.321208 gphoto2-port(0): Could not find USB device (vendor 0x5ca, product 0x2205). Make sure this device is connected to the computer.
0.321288 gphoto2-port(0): Could not find USB device (vendor 0xd96, product 0x4102). Make sure this device is connected to the computer.
0.321367 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.321447 gphoto2-port(0): Could not find USB device (vendor 0x45e, product 0x710). Make sure this device is connected to the computer.
0.321527 gphoto2-port(0): Could not find USB device (vendor 0x84d, product 0x3). Make sure this device is connected to the computer.
0.321606 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.321686 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.341836 get_MS_OSD(3): Hexdump of 128 = 0x80 bytes follows:
0000  80 06 ee 03 00 00 e8 03-01 00 00 00 00 00 00 00  ................
0010  69 00 63 00 01 02 40 00-00 07 05 82 02 40 00 00  i.c...@......@..
0020  00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00  ................
0030  00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00  ................
0040  00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00  ................
0050  00 00 00 00 00 00 00 00-00 00 00 00 00 00 00 00  ................
0060  00 00 00 00 55 53 42 53-00 00 00 00 1c 00 00 00  ....USBS........
0070  00 00 00 00 00 00 00 00-00 00 05 00 00 01 00 00  ................

0.342061 gphoto2-port(0): Could not find USB device (class 0x29a, subclass 0xffffffff, protocol 0xffffffff). Make sure this device is connected to the computer.
0.342160 gphoto2-port(0): Could not find USB device (vendor 0x55f, product 0xc200). Make sure this device is connected to the computer.
0.342242 gphoto2-port(0): Could not find USB device (vendor 0x55f, product 0xa350). Make sure this device is connected to the computer.
0.342322 gphoto2-port(0): Could not find USB device (vendor 0x55f, product 0xc220). Make sure this device is connected to the computer.
0.342403 gphoto2-port(0): Could not find USB device (vendor 0x55f, product 0xc420). Make sure this device is connected to the computer.
0.342483 gphoto2-port(0): Could not find USB device (vendor 0x55f, product 0xc520). Make sure this device is connected to the computer.
0.342564 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x905c). Make sure this device is connected to the computer.
0.342644 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x302). Make sure this device is connected to the computer.
0.342725 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x117). Make sure this device is connected to the computer.
0.342805 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x116). Make sure this device is connected to the computer.
0.342886 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x122). Make sure this device is connected to the computer.
0.342968 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x109). Make sure this device is connected to the computer.
0.343048 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x108). Make sure this device is connected to the computer.
0.343128 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x115). Make sure this device is connected to the computer.
0.343208 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x121). Make sure this device is connected to the computer.
0.343287 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x111). Make sure this device is connected to the computer.
0.343367 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x110). Make sure this device is connected to the computer.
0.343447 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x11d). Make sure this device is connected to the computer.
0.343527 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x12d). Make sure this device is connected to the computer.
0.343607 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x204). Make sure this device is connected to the computer.
0.343687 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x10f). Make sure this device is connected to the computer.
0.343767 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x10e). Make sure this device is connected to the computer.
0.343978 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x10b). Make sure this device is connected to the computer.
0.344058 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x130). Make sure this device is connected to the computer.
0.344138 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x131). Make sure this device is connected to the computer.
0.344219 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x129). Make sure this device is connected to the computer.
0.344299 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x113). Make sure this device is connected to the computer.
0.344379 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x206). Make sure this device is connected to the computer.
0.344459 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x119). Make sure this device is connected to the computer.
0.344539 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x12e). Make sure this device is connected to the computer.
0.344619 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x10d). Make sure this device is connected to the computer.
0.344699 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x135). Make sure this device is connected to the computer.
0.344780 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x103). Make sure this device is connected to the computer.
0.344859 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x112). Make sure this device is connected to the computer.
0.344940 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x102). Make sure this device is connected to the computer.
0.345020 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x104). Make sure this device is connected to the computer.
0.345100 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x208). Make sure this device is connected to the computer.
0.345179 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x41a). Make sure this device is connected to the computer.
0.345259 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x305). Make sure this device is connected to the computer.
0.345339 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x140). Make sure this device is connected to the computer.
0.345419 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x142). Make sure this device is connected to the computer.
0.345499 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x14e). Make sure this device is connected to the computer.
0.345579 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x202). Make sure this device is connected to the computer.
0.345658 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x401). Make sure this device is connected to the computer.
0.345738 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x404). Make sure this device is connected to the computer.
0.345818 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x408). Make sure this device is connected to the computer.
0.345898 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x40a). Make sure this device is connected to the computer.
0.345977 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x402). Make sure this device is connected to the computer.
0.346058 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x410). Make sure this device is connected to the computer.
0.346138 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x406). Make sure this device is connected to the computer.
0.346218 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x40e). Make sure this device is connected to the computer.
0.346297 gphoto2-port(0): Could not find USB device (vendor 0x4b0, product 0x412). Make sure this device is connected to the computer.
0.346377 gphoto2-port(0): Could not find USB device (vendor 0x4fc, product 0x504a). Make sure this device is connected to the computer.
0.346458 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x105). Make sure this device is connected to the computer.
0.346538 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x100). Make sure this device is connected to the computer.
0.346617 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x100). Make sure this device is connected to the computer.
0.346697 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x105). Make sure this device is connected to the computer.
0.346776 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x100). Make sure this device is connected to the computer.
0.346856 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x105). Make sure this device is connected to the computer.
0.346936 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x114). Make sure this device is connected to the computer.
0.347016 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x114). Make sure this device is connected to the computer.
0.347096 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x109). Make sure this device is connected to the computer.
0.347176 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x105). Make sure this device is connected to the computer.
0.347256 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x105). Make sure this device is connected to the computer.
0.347336 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x114). Make sure this device is connected to the computer.
0.347416 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x114). Make sure this device is connected to the computer.
0.347496 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x105). Make sure this device is connected to the computer.
0.347575 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x105). Make sure this device is connected to the computer.
0.347655 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x105). Make sure this device is connected to the computer.
0.347737 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x109). Make sure this device is connected to the computer.
0.347937 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x114). Make sure this device is connected to the computer.
0.348017 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x114). Make sure this device is connected to the computer.
0.348098 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x114). Make sure this device is connected to the computer.
0.348178 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x113). Make sure this device is connected to the computer.
0.348257 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x114). Make sure this device is connected to the computer.
0.348337 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x114). Make sure this device is connected to the computer.
0.348417 gphoto2-port(0): Could not find USB device (vendor 0x7b4, product 0x109). Make sure this device is connected to the computer.
0.348497 gphoto2-port(0): Could not find USB device (vendor 0x919, product 0x100). Make sure this device is connected to the computer.
0.348577 gphoto2-port(0): Could not find USB device (vendor 0x919, product 0x100). Make sure this device is connected to the computer.
0.348658 gphoto2-port(0): Could not find USB device (vendor 0x4da, product 0x2374). Make sure this device is connected to the computer.
0.348738 gphoto2-port-usb(1): Looking for USB device (vendor 0x4da, product 0x2372)... found.
0.348816 gphoto2-port-usb(1): USB device (vendor 0x4da, product 0x2372) is a mass storage device, and might not function with gphoto2. Reference: http://www.linux-usb.org/USB-guide/x498.html
0.348891 gphoto2-port-usb(1): Detected defaults: config 1, interface 0, altsetting 0, inep 82, outep 01, intep ffffffff, class 08, subclass 06
0.348966 gphoto2-abilities-list.c(2): Found 'Panasonic DMC-FZ20 (alternate id)' (0x4da,0x2372)
0.349051 gphoto2-port(2): Freeing port...
0.349131 gphoto2-port(2): Closing port...
0.349385 gphoto2-camera(2): Setting abilities ('Panasonic DMC-FZ20 (alternate id)')...
0.349479 setting/gphoto2-setting.c(2): Creating $HOME/.gphoto
0.349685 setting/gphoto2-setting.c(2): Loading settings from file "/home/james/.gphoto/settings"
0.349788 gphoto2-setting(2): Setting key 'model' to value 'Panasonic DMC-FZ20 (alternate id)' (gphoto2)
0.349868 gphoto2-setting(2): Saving 2 setting(s) to file "/home/james/.gphoto/settings"
0.350084 gphoto2-port-info-list(2): Using ltdl to load io-drivers from '/usr/lib/libgphoto2_port/0.7.0'...
0.350234 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.7.0/disk'.
0.353200 gphoto2-port/disk(2): found 4 volumes
0.371007 gphoto2-port-info-list(2): Loaded 'Media 'Volume (vfat)'' ('disk:/media/transfer') from '/usr/lib/libgphoto2_port/0.7.0/disk'.
0.371146 gphoto2-port-info-list(2): Loaded 'Media 'Volume (ext3)'' ('disk:/') from '/usr/lib/libgphoto2_port/0.7.0/disk'.
0.371223 gphoto2-port-info-list(2): Loaded 'Media 'Windows'' ('disk:/media/windows') from '/usr/lib/libgphoto2_port/0.7.0/disk'.
0.371299 gphoto2-port-info-list(2): Loaded '' ('^disk:') from '/usr/lib/libgphoto2_port/0.7.0/disk'.
0.371377 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.7.0/ptpip'.
0.371648 gphoto2-port-info-list(2): Loaded 'PTP/IP Connection' ('ptpip:') from '/usr/lib/libgphoto2_port/0.7.0/ptpip'.
0.371738 gphoto2-port-info-list(2): Loaded '' ('^ptpip') from '/usr/lib/libgphoto2_port/0.7.0/ptpip'.
0.371919 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.372099 gphoto2-port-serial(2): Trying to lock '/dev/ttyS0'...
0.372248 gphoto2-port-serial(2): Trying to lock '/dev/ttyS1'...
0.372348 gphoto2-port-serial(2): Trying to lock '/dev/ttyS2'...
0.372448 gphoto2-port-serial(2): Trying to lock '/dev/ttyS3'...
0.372633 gphoto2-port-info-list(2): Loaded 'Serial Port 0' ('serial:/dev/ttyS0') from '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.372714 gphoto2-port-info-list(2): Loaded 'Serial Port 1' ('serial:/dev/ttyS1') from '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.372791 gphoto2-port-info-list(2): Loaded 'Serial Port 2' ('serial:/dev/ttyS2') from '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.372866 gphoto2-port-info-list(2): Loaded 'Serial Port 3' ('serial:/dev/ttyS3') from '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.372942 gphoto2-port-info-list(2): Loaded '' ('^serial') from '/usr/lib/libgphoto2_port/0.7.0/serial'.
0.373018 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.7.0/usb'.
0.373622 gphoto2-port-info-list(2): Loaded 'Universal Serial Bus' ('usb:') from '/usr/lib/libgphoto2_port/0.7.0/usb'.
0.373723 gphoto2-port-info-list(2): Loaded '' ('^usb:') from '/usr/lib/libgphoto2_port/0.7.0/usb'.
0.373807 gphoto2-port-info-list(2): Counting entries (13 available)...
0.373884 gphoto2-port-info-list(2): 9 regular entries available.
0.373963 gphoto2-port-info-list(2): Looking for path 'usb:' (13 entries available)...
0.374043 gphoto2-port-info-list(2): Getting info of entry 8 (13 available)...
0.374123 gphoto2-camera(2): Setting port info for port 'Universal Serial Bus' at 'usb:'...
0.374603 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.374697 gphoto2-port(2): Setting settings...
0.374771 gphoto2-setting(2): Setting key 'port' to value 'usb:' (gphoto2)
0.374847 gphoto2-setting(2): Saving 2 setting(s) to file "/home/james/.gphoto/settings"
0.375305 gphoto2-camera(2): Listing files in '/'...
0.375429 gphoto2-camera(2): Initializing camera...
0.375516 gphoto2-port-usb(1): Looking for USB device (vendor 0x4da, product 0x2372)... found.
0.375609 gphoto2-port-usb(1): USB device (vendor 0x4da, product 0x2372) is a mass storage device, and might not function with gphoto2. Reference: http://www.linux-usb.org/USB-guide/x498.html
0.375688 gphoto2-port-usb(1): Detected defaults: config 1, interface 0, altsetting 0, inep 82, outep 01, intep ffffffff, class 08, subclass 06
0.375763 gphoto2-camera(2): Loading '/usr/lib/libgphoto2/2.3.0/ptp2'...
0.376224 gphoto2-port(2): Opening USB port...
0.376378 gphoto2-port(0): Could not query kernel driver of device.
0.376540 gphoto2-port(2): Setting timeout to 8000 millisecond(s)...
0.376628 ptp(2): PTP: Opening session
0.376710 gphoto2-port(2): Writing 16=0x10 byte(s) to port...
0.376792 gphoto2-port(3): Hexdump of 16 = 0x10 bytes follows:
0000  10 00 00 00 01 00 02 10-00 00 00 00 01 00 00 00  ................

8.384371 PTP2/library.c(2): PTP: gp_port_* function returned 0xffffffdd         -35
8.384419 ptp(2): PTP: Opening session
8.384448 gphoto2-port(2): Writing 16=0x10 byte(s) to port...
8.384463 gphoto2-port(3): Hexdump of 16 = 0x10 bytes follows:
0000  10 00 00 00 01 00 02 10-00 00 00 00 01 00 00 00  ................

16.388788 PTP2/library.c(2): PTP: gp_port_* function returned 0xffffffdd        -35
16.388828 ptp(2): PTP: Opening session
16.388857 gphoto2-port(2): Writing 16=0x10 byte(s) to port...
16.388872 gphoto2-port(3): Hexdump of 16 = 0x10 bytes follows:
0000  10 00 00 00 01 00 02 10-00 00 00 00 01 00 00 00  ................

24.393245 PTP2/library.c(2): PTP: gp_port_* function returned 0xffffffdd        -35
24.393321 context(0): PTP I/O error

*** Error ***              
PTP I/O error
24.393354 gphoto2-port(2): Closing port...
24.400201 context(0): An error occurred in the io-library ('Unspecified error'): Could not query kernel driver of device.

*** Error ***              
An error occurred in the io-library ('Unspecified error'): Could not query kernel driver of device.
*** Error (-1: 'Unspecified error') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug --get-all-files

Please make sure there is sufficient quoting around the arguments.

24.400472 gp-camera(2): Freeing camera...
24.400486 gphoto2-port(2): Freeing port...
24.400497 gphoto2-port(2): Closing port...
24.400548 libgphoto2/gphoto2-filesys.c(2): Clearing fscache LRU list...
24.400558 libgphoto2/gphoto2-filesys.c(2): fscache LRU list already empty
24.400567 gphoto2-filesystem(2): Internally deleting all folders from '/'...
james@james:~$ 
```

Is there a way to make this camera play nice with Ubuntu?

---

### Post by rare HERO on 2007-08-05
I'm having a similar problem.  When I plug in and turn on my Nikon Coolpix 4600 the picture import window pops up displaying this: 

```
An error occurred in the io-library ('Unspecified error'): Could not query kernel driver of device.
```

Window will not import photos.

I'm using Ubuntu 7.04.

---

