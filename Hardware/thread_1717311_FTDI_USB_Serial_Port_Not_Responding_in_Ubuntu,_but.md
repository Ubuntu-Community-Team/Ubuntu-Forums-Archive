---
title: "FTDI USB Serial Port Not Responding in Ubuntu, but working in Windows"
date: 2011-03-29
forum: Hardware
---

### Post by TPWT on 2011-03-29
Hello all!

Bit of a pickle- I have a piece of serial hardware I cannot connect to via Ubuntu anymore (used to work with same code back in January 2011).

The setup is a serial device connected to a serial cable, to a FTDI serial converter.

The serial device outputs a constant stream on information using these settings:

BAUD_9600, 
CHAR_SIZE_8, 
PARITY_NONE, 
STOP_BITS_1, 
FLOW_CONTROL_NONE


On windows, I get the test message appearing in a serial terminal with the above settings.

However when I try to do this in Linux with cutecom no response.

To add to the confusion the port seems correctly setup:

lsusb:
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0eef:480d D-WAV Scientific Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 014: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 13d3:5111 IMC Networks Integrated Webcam
Bus 001 Device 003: ID 1415:2000 Nam Tai E&E Products Ltd. or OmniVision Technologies, Inc. Sony Playstation Eye
Bus 001 Device 002: ID 1415:2000 Nam Tai E&E Products Ltd. or OmniVision Technologies, Inc. Sony Playstation Eye
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

dmsg:
```

[ 4060.789194] usb 2-1: new full speed USB device using uhci_hcd and address 14
[ 4060.988321] ftdi_sio 2-1:1.0: FTDI USB Serial Device converter detected
[ 4060.988479] usb 2-1: Detected FT232RL
[ 4060.988493] usb 2-1: Number of endpoints 2
[ 4060.988505] usb 2-1: Endpoint 1 MaxPacketSize 64
[ 4060.988517] usb 2-1: Endpoint 2 MaxPacketSize 64
[ 4060.988528] usb 2-1: Setting MaxPacketSize 64
[ 4060.989711] usb 2-1: FTDI USB Serial Device converter now attached to ttyUSB0

```


I tried my own code (used to work), but to no avail:

```

#include <iostream>
#include <SerialStream.h>
using namespace LibSerial;
using namespace std;

int main()

{
    char byte;

        //connect to ttyUSB0
        SerialPort mySerialPort("/dev/ttyUSB0");

        //open
        mySerialPort.Open(SerialPort::BAUD_9600,  SerialPort::CHAR_SIZE_8, SerialPort::PARITY_NONE,  SerialPort::STOP_BITS_1, SerialPort::FLOW_CONTROL_NONE);

while(1){
        cout << "In" << endl;

        //read with a timeout of 500 ms
        byte = mySerialPort.ReadByte(10000);

        cout << byte << endl;

/*
        cout << "Out" << endl;
        //write a byte
        mySerialPort.WriteByte(0xbfb9694c);
*/

        cout << "Done" << endl;
}

        //close port
        mySerialPort.Close();

        cout << "Closed" << endl;

    return 0;
}

```

which gives:

```

In
&#65533;
Done
In
terminate called after throwing an instance of 'SerialPort::ReadTimeout'
  what():  Read timeout

```

Please help this is for a big project of mine and the deadline is approaching. I had code working in January, but the same code, on the same hardware, in the same room, no longer works.

---

### Post by TPWT on 2011-03-30
It appears to be some kind of handshaking problem.

When I run gtkterm I get nothing

however toggling the DTR suddenly allows data to be sent/recieved.

Does anyone know how to do this with libserial?

---

### Post by piggoy on 2011-06-06
I have exactly the same issue here. I am trying to use a FTDI chip USB-Serial converter with VAG-COM (VCDS-Lite) to read fault codes from my car. The symptoms are exactly as you describe with your code; the port allows one write & read of data and then timeout. This bug related to my application has been reported in this thread with no solution, 

[http://ubuntuforums.org/showthread.php?t=220200&page=2](http://ubuntuforums.org/showthread.php?t=220200&page=2)

This is really annoying and requires me to resort to installing WinXP again on a second partition of my hard drive :( I thought I had shaken off the shackles of microsoft many years ago :(

---

### Post by TPWT on 2011-06-06
It turned out to be a DTR problem for me. 

I came up a bodge, but never a perfect solution.

The DTR line is normally high in Ubuntu, but normally low in windows- we need it to be normally low in order to communicate.

After some hardware hacking and searching for other libraries I used 'gtkterm' to switch the DTR line for me.

I run my script, switch to gtkterm, hit F7 (toggle DTR line) then close gtkterm to prevent duplication errors. 


Not an ideal situation but it'll do.


Oh and use an brand name FTDI cable, that solved a LOT of my problems. Don't understand why it matters, but...

---

### Post by piggoy on 2011-06-06
Thanks for your reply. I'll install gtkterm and try your 'bodge' ;) I'll let you know if it works for me.

---

### Post by NoBugs! on 2012-03-10
I'm noticing this problem in 12.04, it worked fine in 10.04. Where should I file a bug report?

---

### Post by Patrick Voelker on 2012-05-17
After having a problem writing out bytes in 12.04 (reads were ok), I finally found this thread and noticed that I could use minicom to disable hardware flow control and enable software flow control. 

That took care of the issue for my particular application.

This line does the same thing using stty instead of starting up minicom:
stty -F /dev/ttyUSB0 -crtscts ixon ixoff

This may be a different problem and solution but it took me about 3 days to figure out.  :-(

---

### Post by cjiph on 2012-12-24
Thanks to this thread I was able to figure out that a problem I was having with another FTDI device was related to various tty flags changing their defaults between Ubuntu/kernel/FTDI driver releases.

For the reference of anyone else experiencing similar issues, I was able to find out exactly which flags were causing the issue by running stty -a and -g on my old, working, system.

-g is used to dump a machine-readable string which can be used later as an stty command-line argument to reapply exactly the same settings on the new system. This makes for a quick fix to get things up and running again.

-a gives human-readable output which can be used to figure exactly which flags have changed.

---

