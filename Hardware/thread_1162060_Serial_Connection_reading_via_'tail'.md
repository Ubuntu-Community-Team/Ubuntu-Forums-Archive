---
title: "Serial Connection reading via 'tail'"
date: 2009-05-17
forum: Hardware
---

### Post by etar78 on 2009-05-17
All,

I am relatively new to the Ubuntu scene, but have been able to solve most of my problems with some google searches...  Now I'm totally stumped.

I have been using a serial connection (/dev/ttyS0) to log events from my home alarm.  My alarm out is via a DSC PC5401 module which works similar to a GPS unit streaming NEMA data via RS-232.  My various shell (and a little python) scripts have been logging and parsing my logs fine for several months -- until the power went out.

Apparently, I had made a change to the port config which wasn't saved to survive reboot.  Now I've been spending a week googling all sorts of tools and options I had no recollection of using.

I can see the output via minicom now, but used to be able to see it with a simple call to tail.  Now, tail only stalls waiting for data on the line.

I the serial connection is 9600 baud, 8 bit words, with no error correction. (One stop bit is used when using minicom, but isn't specified in the module documentation)

Attached below are snippets of current config.  I've changed the baud rate to 9600 using setserial, but to no avail.  I reset back to default of 115200.

I should also mention I've been running all my config changes and tails as root or another user of the dialout group.

```

#Python snippet
#using pySerial to send commands via serial

def initSerial( ):
    ser = serial.Serial(
        port       = '/dev/ttyS0',
        baudrate   = 9600,
        parity     = serial.PARITY_NONE,
        stopbits   = serial.STOPBITS_ONE,
        bytesize   = serial.EIGHTBITS
    );

    ser.open();
    ser.isOpen();
    ser.flushInput();
    return ser;

def runInputConsole( ):

    ser = initSerial( );
    input=1;
    while 1 :
        out = '';
        # get keyboard input
        input = raw_input(">>>> ")
        if input == 'exit':
                closeSerial( ser );
                break;
        else:
                # send the character to the device
                ser.write( appendCRLF(appendChecksum(input)) );
                time.sleep(5);
                readOutput();

``````
etar@rufus:/opt/PC5401$ setserial /dev/ttyS0 -a
/dev/ttyS0, Line 0, UART: 16550A, Port: 0x03f8, IRQ: 4
    Baud_base: 115200, close_delay: 50, divisor: 0
    closing_wait: 3000
    Flags: spd_normal skip_test

etar@rufus:/opt/PC5401$ 
``````

etar@rufus:/opt/PC5401$ stty -F /dev/ttyS0 -a
speed 9600 baud; rows 0; columns 0; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>;
eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;
werase = ^W; lnext = ^V; flush = ^O; min = 0; time = 0;
-parenb -parodd cs8 -hupcl -cstopb cread clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr -icrnl -ixon -ixoff
-iuclc -ixany -imaxbel -iutf8
-opost -olcuc -ocrnl -onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
-isig -icanon -iexten -echo -echoe -echok -echonl -noflsh -xcase -tostop -echoprt
-echoctl -echoke
etar@rufus:/opt/PC5401$ 
```Any help is very much appreciated.

Thanks!

--etar

---

