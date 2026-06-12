---
title: "ioctl command and i2c"
date: 2019-08-22
forum: Hardware
---

### Post by redmary on 2019-08-22
Hi guys 

I have to programm some devices. Those devices are connected to my linux control unit [LEFT][COLOR=#666666][FONT=Arial]through usb-i2c brigde. 
For example, one side I have PCA9550 led ( [LEFT][COLOR=#101010][FONT=Ubuntu] [/FONT][/COLOR][/LEFT][https://www.nxp.com/docs/en/data-sheet/PCA9550.pdf](https://www.nxp.com/docs/en/data-sheet/PCA9550.pdf)[LEFT][COLOR=#101010][FONT=Ubuntu]? )  and the other side I have my control unit.
My control unit sends ioctl commands to bridge such as:  

 else if (cmd == IOCTL_DEVICE_CMD_I2CWRITE) {
        struct device_i2cwrite s_i2cwrite;
        
        s_i2cwrite.deviceaddress = value;
        s_i2cwrite.deviceconfiguration = 0x01;
        s_i2cwrite.registeraddress = 0x20;
        s_i2cwrite.numdata = 4;
        s_i2cwrite.data[0] = 0x21;
        s_i2cwrite.data[1] = 0x22;
        s_i2cwrite.data[2] = 0x23;
        s_i2cwrite.data[3] = 0x24;
        
        ioctl(m_fddevice, cmd, &s_i2cwrite);
        
    } else if (cmd == IOCTL_DEVICE_CMD_I2CREAD) {
        struct device_i2cread s_i2cread;
        ioctl(m_fddevice, cmd, &s_i2cread);
        
        _INF() << "number readed = " << '0' + s_i2cread.numdata;
        _INF() << HEX1(s_i2cread.data[0]) << " " << HEX1(s_i2cread.data[1]) << " " << HEX1(s_i2cread.data[2]) << " " << HEX1(s_i2cread.data[3]);
        _INF() << '0'+s_i2cread.data[0] << " " << '0'+s_i2cread.data[1] << " " << '0'+s_i2cread.data[2] << " " << '0'+s_i2cread.data[3];
        
    }

But I m not able to use that. 

You have suggests? 

thanks 
kiss 
Mary [B][I][U][SUB][SUP]
[/SUP][/SUB][/U][/I][/B][/FONT][/COLOR][/LEFT][/FONT][/COLOR][/LEFT]

---

