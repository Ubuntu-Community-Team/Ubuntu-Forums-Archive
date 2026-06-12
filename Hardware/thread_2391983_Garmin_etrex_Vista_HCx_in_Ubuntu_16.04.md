---
title: "Garmin etrex Vista HCx in Ubuntu 16.04"
date: 2018-05-15
forum: Hardware
---

### Post by thenanodude2 on 2018-05-15
I just spent several hours trying to get my legacy Garmin etrex Vista HCx to work in Ubuntu 16.04.  There were several issues that needed to be addressed, and a couple fixes are a little different than in previous versions of Ubuntu, so I thought I'd record my solution here.
1. Turn on the GPS and plug it into a USB port on your computer.  Ensure it is recognized as a USB device
    - in a terminal run
      > lsusb
    - you should see an entry like: 
               > Bus **001** Device **018**: ID 091e:0003 Garmin International GPS (various models)
    - note the bus and device numbers (I bolded them in the line above)

   - One more check: run "dmesg" in a terminal.  You should see several lines of usb information, including one like:
               > [ 5321.455772] usb 1-4: New USB device found, idVendor=091e, idProduct=0003

2. Double check the module "garmin_gps" does not load:
   - in a terminal, run 
       > lsmod | grep gps
   - this should produce no output.  
   - If it does show that garmin_gps is running, remove the module with:
          > sudo modeprobe - r garmin_gps

   - To permanently prevent garmin_gps from loading: 
          - edit /etc/modprobe.d/blacklist:
                  > sudo leafpad  /etc/modprobe.d/blacklist
          - add the following line to the blacklist:
                  > # prevent garmin_gps from being loaded so generic USB can be used instead
                  blacklist garmin_gps


3. Check the permissions of the newly created /dev point.  This will be in /dev/bus/usb/**BUS**/**DEVICE**, where "BUS" and "DEVICE" are the numbers from the lsusb command (bolded above).  Note that in my command below, BUS = 001
    - in a terminal run
        > ls -al /dev/bus/usb/001/*

    - You will probably see something like (note my bolded DEVICE number below):
        > crw-rw-r-- 1 root root 189, 19 May 15 09:55 **018**

    - If you see something like the above, your group and permissions will not properly let you access the GPS device. Proceed to step 4

4. Create a udev rule that gives you permission to access the device automatically when mounted:
   - use sudo to create and edit /etc/udev/rules.d/51-garmin.rules
        > sudo leafpad /etc/udev/rules.d/51-garmin.rules

   - in this text file, enter the following line:
    > SUBSYSTEM=="usb", ATTR{idVendor}=="091e", ATTRS{idProduct}=="0003" MODE="0666", GROUP="plugdev"

   - reload the udev rules: 
     > sudo udevadm control --reload-rules

5. Unplug and then re-plug your GPS device (note: you will probably see the screen go dark after a second or two), then check its connectivity
    - Run "lsusb" and "dmesg" as in step 1.  You will may note the DEVICE number has changed from the first time (note that mine incremented to 019)
    - Check the permissions, as in step 2: 
        > ls -al /dev/bus/usb/001/*

    - You should now see something like:
        > crw-rw-rw- 1 root plugdev 189, 20 May 15 10:04 **019**

6. Ensure that you are in the group "plugdev"
    - in the terminal, run:
       > groups

    - If you do not see the group "plugdev" in the list, add yourself to it:
       > sudo adduser USER plugdev

    - Run "groups" again to check that you are a user.  You may need to logout and login for it to take effect

7. Blacklist the Garmin GPS in the power settings file (NOTE: this was the thing that took the longest to figure out!)
    - Edit the file /etc/default/tlp
         > sudo leafpad /etc/default/tlp

    - Search for "USB_BLACKLIST" and add the idVendor:idProduct number, as :
        > USB_BLACKLIST="091e:0003"

    - Note that if any other devices are already listed in the blacklist, you should add this to the list with a space in between, for example:
        > USB_BLACKLIST="XXXX:YYYY 091e:0003"

8. Unplug and re-plug in the Garmin GPS.  This time, the screen should NOT go dark after a second!  If so, you are connected!  However, you will still need some kind of program to access the device.

9. The program GPSBabel is recommended.  You can download it from the website, or install it from the repos.  I recommend getting the GUI to go with it:
     - Download from [https://www.gpsbabel.org/index.html](https://www.gpsbabel.org/index.html)
     - Install from repos:
        > sudo apt-get install gpsbabel gpsbabel-gui

     - To manually double check that the Garmin GPS is accessible, in a terminal, run:
           > gpsbabel -i garmin -f usb:-1

     - You should see something like:
        > 0 3382731428 694 eTrex Vista HCx Software Version 2.40

     - To run the GUI, from a terminal type:
       > gpsbabelfe

     - In the GPSBabel program, select the "Device" radio button for the input or output. At this point, you should see "Garmin serial/USB protocol" in the dropdown menu.  Ensure the device name is set to "usb:", and you should be all set! :guitar:
         

Sites used to figure this all out:
[https://wiki.openstreetmap.org/wiki/USB_Garmin_on_GNU/Linux](https://wiki.openstreetmap.org/wiki/USB_Garmin_on_GNU/Linux)
[https://forum.siduction.org/index.php?topic=4990.0](https://forum.siduction.org/index.php?topic=4990.0)
[https://www.gpsbabel.org/index.html](https://www.gpsbabel.org/index.html)

---

