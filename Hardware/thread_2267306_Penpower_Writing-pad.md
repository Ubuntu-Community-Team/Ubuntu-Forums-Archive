---
title: "Penpower Writing-pad"
date: 2015-02-28
forum: Hardware
---

### Post by maryip on 2015-02-28
Hi. I have a penpower writing pad that I brought a long time ago.
I would be happy enough to make it work like a mouse. How to do that?

Lubuntu can detect it when I connect it by usb:
[FONT=courier new]
$ lsusb[/FONT][INDENT][FONT=courier new]Bus 002 Device 004: ID 0cf3:3004 Atheros Communications, Inc.
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:288f Sunplus Innovation Technology Inc.
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
[COLOR=#0000FF]Bus 003 Device 003: ID 1267:0701 Logic3 / SpectraVideo plc
[/COLOR]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/FONT][/INDENT]
[FONT=courier new]$ dmesg | grep "1267:0701"[/FONT][INDENT][FONT=courier new][ 3414.632180] hid-generic 0003:1267:0701.0001: hiddev0,hidraw0: USB HID v1.10 Device [[COLOR=#0000ff]ELAN TouchPad[/COLOR]] on usb-0000:00:14.0-1/input0
[ 3931.844464] hid-generic 0003:1267:0701.0002: hiddev0,hidraw0: USB HID v1.10 Device [ELAN TouchPad] on usb-0000:00:14.0-1/input0[/FONT]
[/INDENT]

But, xinput doesn't show the device, because its output doesn't change when I disconnect the touchpad from the laptop.
[FONT=courier new]$ xinput
[/FONT][INDENT][FONT=courier new]
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;     &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; CyPS/2 Cypress Trackpad                     id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
       &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
       &#8627; Power Button                                id=6    [slave  keyboard (3)]
       &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
       &#8627; Power Button                                id=8    [slave  keyboard (3)]
       &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
       &#8627; Laptop_Integrated_Webcam_1.3M               id=10    [slave  keyboard (3)]
       &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
       &#8627; Dell WMI hotkeys                            id=13    [slave  keyboard (3)]
[/FONT][/INDENT]

My laptop's kernel version is:
[FONT=courier new]$ uname -r
[/FONT][INDENT][FONT=courier new]3.17.4-031704-lowlatency
[/FONT][/INDENT]

Thank you for your help.


[SIZE=4]Test 1:[/SIZE][INDENT] I tried the instruction at [http://ubuntuforums.org/showthread.php?t=1103792&highlight=penpower](http://ubuntuforums.org/showthread.php?t=1103792&highlight=penpower)
But when I create a /etc/X11/xorg.conf file (there was not a xorg.conf file there) with the Section "InputDevice"... lines, Lubuntu can not start the desktop environment.
[/INDENT]
> [INDENT=2]**[SIZE=2][IMG]http://ubuntuforums.org/images/icons/icon10.png[/IMG] Re: Tooya Pro tablet on Ubuntu?         [/SIZE]**
[SIZE=2]Solved it! :razz: I followed the instructions on [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom), and then changed my xorg.conf file, and it now works perfectly. The lines I added to xorg.conf are shown below:[/SIZE]
```

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
EndSection
Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "pad"
  Option        "USB"           "on"
EndSection
Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "pad"
EndSection

```
[/INDENT]


[SIZE=4]Test 2:[/SIZE][INDENT][http://www.linuxquestions.org/questions/linux-hardware-18/how-does-linux-handle-usb-mouse-634247/](http://www.linuxquestions.org/questions/linux-hardware-18/how-does-linux-handle-usb-mouse-634247/)
$ sudo cat /dev/usb/hiddev0 
gives some unicode characters when I write on the writing-pad.

Tried the xtestmotion.c on the link, after installing xorg-dev with apt-get.
Assertion failed when I run the compiled program without sudo.

Running the program with sudo and in terminal emulator(lxterminal) give the following output:
[/INDENT]
[INDENT]Problem: The mouse stayed near top left corner x.x
```

/* gcc -g -Wall -o xtestmotion xtestmotion.c -L /usr/X11R6/lib/ -lX11 -lXtst */

#include <stdio.h>
#include <stdlib.h>
#include <assert.h>
#include <X11/extensions/XTest.h>

int main( int argc, char *argv[] ) {
        int pad_x = 128, pad_y = 240, pad_width=1184, pad_height=1040;
        int canvas_x = 0, canvas_y = 0, canvas_width=1024, canvas_height=768;
        int x,y;
        Display *dpy;
        int i;
        FILE *hiddev;
        int packet[12];
        int state=0;

        dpy = XOpenDisplay( NULL );
        assert(dpy);

        hiddev = fopen("/dev/usb/hiddev0", "r");
        assert(hiddev);

        for(;;)
        {
                for(i=0; i<12; i++) {
                        packet[i] = getc(hiddev);
                        packet[i] += getc(hiddev)*0x100;
                        packet[i] += getc(hiddev)*0x10000;
                        packet[i] += getc(hiddev)*0x1000000;
                        printf("\t%x", packet[i]);
                }
                printf("\n");
                if(packet[1] != 0 && packet[3] != 0) {
                        x = (packet[1]-pad_x)*canvas_width/pad_width + canvas_x;
                        y = (packet[3]-pad_y)*canvas_height/pad_height + canvas_y;
                        XTestFakeMotionEvent(dpy, -1, x, y, CurrentTime);
                        printf("\t(x,y): (%d,%d)\n", x, y);
                        if(state==0) {
                                XTestFakeButtonEvent(dpy, 1, 1, CurrentTime);
                                state=1;
                        }
                }
                else {
                        if(state==1) {
                                XTestFakeButtonEvent(dpy, 1, 0, CurrentTime);
                                state=0;
                        }
                }
                XFlush(dpy);
        }
        return 0;
}

```
Output from the program:[FONT=courier new]

    [/FONT][/INDENT]
[INDENT=2][FONT=courier new](x,y): (-29,-175)
    d0000    2    d0000    60    d0000    2    d0000    0    d0000    0    d0000    80
    (x,y): (-108,-106)
    d0000    bd    d0000    2    d0000    61    d0000    2    d0000    0    d0000    0
    (x,y): (52,-175)
    d0000    80    d0000    b8    d0000    2    d0000    62    d0000    2    d0000    0
    (x,y): (0,-41)
    d0000    0    d0000    0    d0000    b8    d0000    2    d0000    62    d0000    2
    d0000    0    d0000    0    d0000    0    d0000    b8    d0000    2    d0000    62 [/FONT]
[/INDENT]
[SIZE=4]Test 3:[/SIZE][INDENT]Made a /etc/X11/xorg.conf file with the following. Lubuntu can go to desktop environment, but xinput shows no new input device... and that didn't work.
[FONT=courier new] Section "InputDevice"
    Driver "touchkitusb"
    Identifier "stylus"
    Option "Device" "/dev/usb/hiddev0"
    Option "Type" "stylus"
    Option "ForceDevice" "ISDV4" # dunno about this bit.
EndSection 
[/FONT]
This page say should use "usbhid" instead of "touchkitusb"
[https://lists.ubuntu.com/archives/ubuntu-users/2009-November/201994.html](https://lists.ubuntu.com/archives/ubuntu-users/2009-November/201994.html)
[FONT=courier new]
[/FONT]
[/INDENT]

---

### Post by maryip on 2015-03-01
The xtestmotion.c didn't really work for my writing pad.


writingpad.c

middle button toggles dragging mode during writing and the writing pad is not calibrated in this program.

```

/* 
This program moves the cursor with the "Penpower Carefree Pen" writing pad.

To compile the program on Lubuntu linux, install xorg-dev, then run:
gcc -g -Wall -o writingpad writingpad.c -L /usr/X11R6/lib/ -lX11 -lXtst

To run:
sudo ./writingpad
*/ 

#include <stdio.h>
#include <stdlib.h>
#include <assert.h>
#include <X11/extensions/XTest.h> 

void print_A(int *A){
    // Print the array for debugging
        int i,j;
    printf("-----------------------\n");
    for (i=0; i<7; i++){
        for (j=0; j<8; j++){
            printf("%d\t", A[i*8+j]);
        }
        printf("\n");
    }
    printf("-----------------------\n");
}

int main( int argc, char *argv[] ) { 

        Display *dpy;
        dpy = XOpenDisplay( NULL );
        assert(dpy); // Check if we have X window.

        FILE *hiddev;
        hiddev = fopen("/dev/usb/hiddev0", "r");
        assert(hiddev); //Check if we can read the device.
                        //if fail, either writing pad is not connected
                        //or we don't have root permission.

        /*
        Normally, the array A should be:
                                           [a] is the button state. 1,2,4 for top, middle, buttom button
                0 ,0,0   [a],0,0,0,0,0,        128 for pen on pad, 0 for release of button or raise of pen.
                13,0,174 [b],0,0,0,0,0,    [b] and [c] give raw x-coordinate
                13,0,2   [c],0,0,0,0,0,        raw_x = b + 256*c
                13,0,249 [d],0,0,0,0,0,    [d] and [e] give raw y-coordinate
                13,0,1   [e],0,0,0,0,0,        raw_y = d + 256*e
                13,0,0      ,0,0,0,0,0,    41-48th elemtns
                13,0,0      ,0,0,0,0,0    Interlude: 49-56th elemtns are filled only at start of next event.

                The 0 and 13 don't change, except that
                occassionally can get incomplete rows like 0,0,13 (wrong alignment).
        */
        int element_index=0;
        int column_index=0;
        int A[56]; //The writing-pad that I get only has integer resolution.

    int button_state;
    int raw_x;
    int raw_y;
    /*
    int pad_x = 128, pad_y = 240, pad_width=1184, pad_height=1040;
    int canvas_x = 0, canvas_y = 0, canvas_width=1024, canvas_height=768;
    int x,y;
    */
    int drag_mode=1;
    int button_guard=0;
    for(;;)
    {
        A[element_index] = getc(hiddev); //Wait until writing-pad sends a char.

        if (element_index == 56 || (A[element_index] == 13 && column_index < 8)){
            //Reset every 56 elements.

            //(A[element_index] == 13 && column_index < 8)
            //Reset unless alignment is as expected. Without this condition,
            //    the useful column may be any column (not just 2nd column).
            column_index=0;
            element_index=0;
        }
        if (element_index == 48){

            print_A(A); ////Debug

            button_state = A[2];
            raw_x = A[10]+A[18]*256;
            raw_y = A[26]+A[34]*256;
            printf("button: %d, raw_x: %d, raw_y: %d\n", button_state, raw_x, raw_y);

            switch(button_state){
                case 128:{
                    //pen on writing-pad. the writing pad can not sense pressure(?).
                    XTestFakeMotionEvent(dpy, -1, raw_x, raw_y, 0); //Move cursor.
                    if (button_guard==0 && drag_mode==1){
                        XTestFakeButtonEvent(dpy, 1, 1, 0); //1 is left mouse button. 1 is pressed.
                        printf("drag start\n");
                        button_guard=128;
                    }
                    break;
                }
                case 0:{
                    //button is released or pen is raised
                    if (button_guard == 128 && drag_mode==1){
                        XTestFakeButtonEvent(dpy, 1, 0, 0); //1 is left button, 1 is released.
                    }
                    button_guard=0;
                    break;
                }    
                case 1:{
                    //only top button is pressed
                    break;
                }
                case 2:{
                    //only middle button is pressed
                    if (button_guard==0){
                        drag_mode=!(drag_mode); //toggle drag_mode
                        button_guard=2;
                        printf("middle button pressed once\n");
                    }
                    //dragging=0;
                    break;
                }
                case 4:{
                    //only bottom button is pressed.
                    break;
                }
            }
            XFlush(dpy); // Ask X to process events.
        }

                //Increase indices of array A
        column_index++;
        element_index++;
    }
    return 0;
}

```

---

