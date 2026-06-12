---
title: "1a86:7523 QinHeng Electronics HL-340 USB-Serial adapter does not work with Ubuntu"
date: 2023-09-08
forum: Hardware
---

### Post by yunzhi-wu on 2023-09-08
Hi! I have got a "1a86:7523 QinHeng Electronics HL-340 USB-Serial adapter".
I am trying to use it on my Nano TX2 platform where Ubuntu 18.04 LTS is running.

I use python3 script with pyserial lib, it does not work. The same script and lib works fine on windows, i.e., bytes can be sent and received via port COM3.

It is ttyUSB0 in my Ubuntu. I can see it is detected. It seems that it can send, but it can not response.

I tried two methods. None of them fixed.

Method 1 is to check the rate. It is correct.[INDENT]sudo stty -F /dev/ttyUSB0 -a[/INDENT]
[INDENT]speed 19200 baud; rows 0; columns 0; line = 0;[/INDENT]
[INDENT]intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>;[/INDENT]
[INDENT]eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;[/INDENT]
[INDENT]werase = ^W; lnext = ^V; discard = ^O; min = 0; time = 0;[/INDENT]
[INDENT]parenb -parodd -cmspar cs8 hupcl -cstopb cread clocal -crtscts[/INDENT]
[INDENT]-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr -icrnl -ixon -ixoff[/INDENT]
[INDENT]-iuclc -ixany -imaxbel -iutf8[/INDENT]
[INDENT]-opost -olcuc -ocrnl -onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0[/INDENT]
[INDENT]-isig -icanon -iexten -echo -echoe -echok -echonl -noflsh -xcase -tostop -echoprt[/INDENT]
[INDENT]-echoctl -echoke -flusho -extproc[/INDENT]


Method 2:[INDENT]sudo modprobe ch341[/INDENT]


My python3 script is like:

```
[INDENT]import serial[/INDENT]
[INDENT]
[/INDENT]
[INDENT]def read_serial_port_info(serial_port):[/INDENT]
[INDENT]    packet = bytearray() # 02 03 00 01 00 04 15 fa[/INDENT]
[INDENT]    packet.append(0x02)[/INDENT]
[INDENT]    packet.append(0x03)[/INDENT]
[INDENT]    packet.append(0x00)[/INDENT]
[INDENT]    packet.append(0x01)[/INDENT]
[INDENT]    packet.append(0x00)[/INDENT]
[INDENT]    packet.append(0x04)[/INDENT]
[INDENT]    packet.append(0x15)[/INDENT]
[INDENT]    packet.append(0xfa)[/INDENT]
[INDENT]
[/INDENT]
[INDENT]    serial_port.write(packet)[/INDENT]
[INDENT]
[/INDENT]
[INDENT]    print('ttyUSB0 write done')[/INDENT]
[INDENT]
[/INDENT]
[INDENT]    while 1:[/INDENT]
[INDENT]        # Wait until there is data waiting in the serial buffer[/INDENT]
[INDENT]        if serial_port.in_waiting > 0:[/INDENT]
[INDENT]            # Read data out of the buffer until a carraige return / new line is found[/INDENT]
[INDENT]            serial_bytes_read = serial_port.read(serial_port.in_waiting)[/INDENT]
[INDENT]            serial_bytes_list_hex = [hex(x).split('x')[-1] for x in serial_bytes_read][/INDENT]
[INDENT]            print(serial_bytes_list_hex)[/INDENT]
[INDENT]            return serial_bytes_list_hex[/INDENT]
[INDENT]            break[/INDENT]
[INDENT]
[/INDENT]
[INDENT]def main():[/INDENT]
[INDENT]    serial_port = serial.Serial([/INDENT]
[INDENT]        port="/dev/ttyUSB0", baudrate=19200, bytesize=8, timeout=20, stopbits=serial.STOPBITS_ONE, parity=serial.PARITY_EVEN[/INDENT]
[INDENT]    )[/INDENT]
[INDENT]    read_serial_port_info(serial_port)[/INDENT]
[INDENT]
[/INDENT]
[INDENT]if __name__ == "__main__":[/INDENT]
[INDENT]    main()[/INDENT]

```
One LED blinks when to write to the converter (same as with windows), but no data come back. (In windows, it always sends data back correctly.)

On this page [https://linux-hardware.org/?id=usb:1a86-7523&page=1](https://linux-hardware.org/?id=usb:1a86-7523&page=1), the device has been detected on Ubuntu. Only four rows "works", does it mean no one has verified it on Ubuntu?

**Any idea what should I try?**

Some info about my ttyUSB0:[INDENT]Bus 001 Device 008: ID 1a86:7523 QinHeng Electronics HL-340 USB-Serial adapter[/INDENT]
[INDENT]Device Descriptor:[/INDENT]
[INDENT]  bLength                18[/INDENT]
[INDENT]  bDescriptorType         1[/INDENT]
[INDENT]  bcdUSB               1.10[/INDENT]
[INDENT]  bDeviceClass          255 Vendor Specific Class[/INDENT]
[INDENT]  bDeviceSubClass         0 [/INDENT]
[INDENT]  bDeviceProtocol         0 [/INDENT]
[INDENT]  bMaxPacketSize0         8[/INDENT]
[INDENT]  idVendor           0x1a86 QinHeng Electronics[/INDENT]
[INDENT]  idProduct          0x7523 HL-340 USB-Serial adapter[/INDENT]
[INDENT]  bcdDevice            2.64[/INDENT]
[INDENT]  iManufacturer           0 [/INDENT]
[INDENT]  iProduct                2 [/INDENT]
[INDENT]  iSerial                 0 [/INDENT]
[INDENT]  bNumConfigurations      1[/INDENT]
[INDENT]  Configuration Descriptor:[/INDENT]
[INDENT]    bLength                 9[/INDENT]
[INDENT]    bDescriptorType         2[/INDENT]
[INDENT]    wTotalLength           39[/INDENT]
[INDENT]    bNumInterfaces          1[/INDENT]
[INDENT]    bConfigurationValue     1[/INDENT]
[INDENT]    iConfiguration          0 [/INDENT]
[INDENT]    bmAttributes         0x80[/INDENT]
[INDENT]      (Bus Powered)[/INDENT]
[INDENT]    MaxPower               98mA[/INDENT]
[INDENT]    Interface Descriptor:[/INDENT]
[INDENT]      bLength                 9[/INDENT]
[INDENT]      bDescriptorType         4[/INDENT]
[INDENT]      bInterfaceNumber        0[/INDENT]
[INDENT]      bAlternateSetting       0[/INDENT]
[INDENT]      bNumEndpoints           3[/INDENT]
[INDENT]      bInterfaceClass       255 Vendor Specific Class[/INDENT]
[INDENT]      bInterfaceSubClass      1 [/INDENT]
[INDENT]      bInterfaceProtocol      2 [/INDENT]
[INDENT]      iInterface              0 [/INDENT]
[INDENT]      Endpoint Descriptor:[/INDENT]
[INDENT]        bLength                 7[/INDENT]
[INDENT]        bDescriptorType         5[/INDENT]
[INDENT]        bEndpointAddress     0x82  EP 2 IN[/INDENT]
[INDENT]        bmAttributes            2[/INDENT]
[INDENT]          Transfer Type            Bulk[/INDENT]
[INDENT]          Synch Type               None[/INDENT]
[INDENT]          Usage Type               Data[/INDENT]
[INDENT]        wMaxPacketSize     0x0020  1x 32 bytes[/INDENT]
[INDENT]        bInterval               0[/INDENT]
[INDENT]      Endpoint Descriptor:[/INDENT]
[INDENT]        bLength                 7[/INDENT]
[INDENT]        bDescriptorType         5[/INDENT]
[INDENT]        bEndpointAddress     0x02  EP 2 OUT[/INDENT]
[INDENT]        bmAttributes            2[/INDENT]
[INDENT]          Transfer Type            Bulk[/INDENT]
[INDENT]          Synch Type               None[/INDENT]
[INDENT]          Usage Type               Data[/INDENT]
[INDENT]        wMaxPacketSize     0x0020  1x 32 bytes[/INDENT]
[INDENT]        bInterval               0[/INDENT]
[INDENT]      Endpoint Descriptor:[/INDENT]
[INDENT]        bLength                 7[/INDENT]
[INDENT]        bDescriptorType         5[/INDENT]
[INDENT]        bEndpointAddress     0x81  EP 1 IN[/INDENT]
[INDENT]        bmAttributes            3[/INDENT]
[INDENT]          Transfer Type            Interrupt[/INDENT]
[INDENT]          Synch Type               None[/INDENT]
[INDENT]          Usage Type               Data[/INDENT]
[INDENT]        wMaxPacketSize     0x0008  1x 8 bytes[/INDENT]
[INDENT]        bInterval               1[/INDENT]

---

### Post by jeremy31 on 2023-09-08
Have you added your user to the dialout group

---

### Post by yunzhi-wu on 2023-09-08
I have just added myself into that group, now I am in that group after I log out and log in:
*groups*
[I]yunzhi adm dialout 
[/I]Still issue remains.

---

