---
title: "problems with usb 2 serial converter"
date: 2010-12-18
forum: Hardware
---

### Post by aworld on 2010-12-18
Hi, all. I am new to this forum,  I have post this question to programming discussion branch, but I dont know if it is a right place to put it, I also think this problem is a hardware problem, so I just post it here again, thanks, everyone.

I got a problem with my usb2serial adpater, it can not read or send anything.

First, Details of my laptop:

I have Dell Studio 15, i5 64 bit. But, I have installed 32 bit 10.04 LTS ubuntu. //** could this be a problem?

Second, my problems:

I have a FTDI usb->serial adapter, I just want to do a simple program which makes it read & write for testing. But, It does not work!!! 

In testing, besides my program, I installed "cutecom", a serial terminal with a GUI interface. I chose "/dev/ttyUSB0" as my device, 8N1,9200 for baudrate..etc I connect this serial port to my win7 64bit desktop, and I configure the COM1 with the same parameters. But no matter what i send, I receive nothing on my Linux side, and no matter what I am trying to send from Linux, I also got nothing on my windows7 screen.... strange....

I also have used a oscilloscope to check the serial port from my win7, It gives me perfect, clean data. (ofc, I connect pin5 as signal ground, and test pin3 as the port for transmitting). When i test my linux serial port, I got something, but the data is ****, looks like a saw teeth all the time, And it seems the data is transmitted 10x faster than windows serial port..... 

More information:

I have checked with command "dmesg | grep usb", it gives me information like "FTDI usb2serial converter has been attached to ttyUSB0".

When using lsusb, i also got the vender ID and product ID.

In order to avoid some permission issue, I run my program and "cutecom" as a root user, but still nothing....

No matter how many bugs my program have, it should at least work with "cutecom", at least show me something on screen, and at least send something readable by another serial terminal..... 

I wont have a nice Chrixmas if I can not solve this problem.... Any advice???

If you need more information, I can post them here.


FYI:

no matter in my program or in some terminal software, I dont have any error message!!!!!!!! No Error at all...............
(If I choose some other device, at least it shows me "opening failed..." or "can not open device" !!!)

for compiling, I am just using gcc...........

---

### Post by efflandt on 2010-12-19
Not so strange.  If you think in audio terms it is like you are trying to talk to the microphone of Windows (instead of its speaker) and likewise Windows is trying to talk to your microphone.

When 2 terminals are trying to talk to each other you need a null modem cable serial or adapter so that what you type on your keyboard (transmit) goes to the screen (receive) of Windows, instead of its transmit wire.  You also need to set your terminal program to echo characters you type locally, because the terminal at the other end is not going to echo them back to you.

So you may be attempting to do TX1<-->TX2 and RX1--RX2.

But with null modem cable or adapter you would be doing TX1-->RX2 and RX1<--TX2

Back in my early computing days Apple would set the high bit of ASCII characters and DOS did not.  So when I was trying to communicate between an Apple ][+ and PC, I had to set the Apple 8N1 and the DOS 7N2 (so it would ignore, but set an extra bit).  That should not be an issue between Linux and Windows, although, if lines of text overlap each other you may need to make configure one or the other terminal so Enter sends carriage return and line feed instead of just carriage return.

---

### Post by IcarusR on 2010-12-19
> When 2 terminals are trying to talk to each other you need a null modem cable

I agree plug a serial null modem cable into your usb/serial converter & try again.

Info here....

[http://www.nullmodem.com/NullModem.htm]("http://www.nullmodem.com/NullModem.htm")

[http://www.nullmodem.com/NullModem.htm]("http://www.nullmodem.com/NullModem.htm")

---

### Post by TPWT on 2011-03-29
Apologies for the bump, but was there any resolution for this problem? I have a simialr story- I have a piece of serial hardware I cannot connect to  via Ubuntu anymore (used to work with same code back in January 2011).

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

```dmsg:
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
        mySerialPort.Open(SerialPort::BAUD_9600,   SerialPort::CHAR_SIZE_8, SerialPort::PARITY_NONE,   SerialPort::STOP_BITS_1, SerialPort::FLOW_CONTROL_NONE);

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

```which gives:

```

In
&#65533;
Done
In
terminate called after throwing an instance of 'SerialPort::ReadTimeout'
  what():  Read timeout

```Please help this is for a big project of mine and the deadline is  approaching. I had code working in January, but the same code, on the  same hardware, in the same room, no longer works.

---

