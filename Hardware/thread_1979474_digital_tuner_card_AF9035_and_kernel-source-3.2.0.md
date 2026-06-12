---
title: "digital tuner card AF9035 and kernel-source-3.2.0"
date: 2012-05-13
forum: Hardware
---

### Post by Amraks on 2012-05-13
Hey I have a digital tuner card AF9035 chip, it was working before I done my update. Then it came up as busy in mythtv, So then I went to the backend of mythtv and it had error unknown.

So I figured I better recompile the drivers after downloading all the essentials like build, kernel source, headers, kernel package.

then I put a few ln -s to the linux-source drivers in my AF9035 source folder so it would compile as normal.

It usually does a few warnings but does not do this. first time I have seen this error.


Having this trouble using kernel-source-3.2.0 linux-headers-3.2.0-24-generic

```
  
/home/media/installer/AF903x_SRC/af903x-devices.c: In function &#8216;af903x_frontend_attach&#8217;:
 /home/media/installer/AF903x_SRC/af903x-devices.c:96:1: warning: control reaches end of non-void function [-Wreturn-type]
    make[2]: *** [/home/media/installer/AF903x_SRC/af903x-devices.o] Error 1
    make[1]: *** [_module_/home/media/installer/AF903x_SRC] Error 2
    make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
    make: *** [default] Error 2

```Anyone got any solutions?

---

### Post by Amraks on 2012-05-13
sudo nano ~/installer/AF903x_SRC/af903x-devices.c

```

#include "af903x.h"

bool  DevicePower;
static int af903x_pid_filter_ctrl(struct dvb_usb_adapter *adap, int onoff)
{
    int ret =0;
#if LINUX_VERSION_CODE >  KERNEL_VERSION(2,6,18)
    deb_data("%s: onoff:%d\n", __func__, onoff);

    if ( PDC->fc[adap->id].bEnPID !=  onoff )
        DL_ResetPID((BYTE)adap->id);

    PDC->fc[adap->id].bEnPID =  onoff;
    
    DL_PIDOnOff((BYTE)adap->id,onoff);
#endif

    return ret;
}

static int af903x_pid_filter(struct dvb_usb_adapter *adap, int index, u16 pidnum,
    int onoff)
{
    int ret = 0;
 #if LINUX_VERSION_CODE >  KERNEL_VERSION(2,6,18)
    Pid pid;
    deb_data("- %s: set pid filter, index %d, pid %x, onoff %d, now_onoff %d.\n",
    __func__, index, pidnum, onoff, PDC->fc[adap->id].bEnPID);

    if (onoff && !PDC->fc[adap->id].bEnPID)
    {
        DL_ResetPID((BYTE)adap->id);
        PDC->fc[adap->id].bEnPID =  onoff;
        DL_PIDOnOff((BYTE)adap->id,onoff);
        pid.sectionType = SectionType_TABLE;
            pid.table = 0x00;
            pid.duration = 0xFF;
    }
    
        pid.value = (Word)pidnum;
    if (onoff){
        ret = DL_AddPID((BYTE)adap->id, index, pid);
    }else{
        ret = DL_RemovePID((BYTE)adap->id, index, pid);
    }
#endif

    return ret;
}

static int af903x_download_firmware(struct usb_device *udev, const struct firmware *fw)
{
    int ret=0;
    deb_data("- Enter %s Function -\n",__FUNCTION__);
    
    return ret;
}

static int af903x_powerctrl(struct dvb_usb_device *d, int onoff)
{

    int ret;
    DevicePower = onoff;

#if LINUX_VERSION_CODE >  KERNEL_VERSION(2,6,18)
    deb_data("- Enter %s Function - chip=%d:%s\n",__FUNCTION__, d->adapter->id, onoff?"ON":"OFF");
    ret = DL_ApCtrl(d->adapter->id, onoff);
#else
    deb_data("- Enter %s Function - %s\n",__FUNCTION__, onoff?"ON":"OFF");
    ret = DL_ApCtrl(0, onoff);
#endif
    if(ret) deb_data("    af903x_powerctrl Fail: 0x%04X\n", ret);

    return ret;
}

static int af903x_identify_state(struct usb_device *udev, struct dvb_usb_device_properties *props,
            struct dvb_usb_device_description **desc, int *cold)
{
    deb_data("- Enter %s Function -\n",__FUNCTION__);
    *cold = 0;

    return 0;
}

static int af903x_frontend_attach(struct dvb_usb_adapter *adap)
{
#if LINUX_VERSION_CODE >  KERNEL_VERSION(2,6,18)
    deb_data("- Enter %s Function - chip=%d\n", __FUNCTION__, adap->id);
#else
     deb_data("- Enter %s Function - \n", __FUNCTION__);
#endif
    adap->fe = af903x_attach(1);    

    return adap->fe == NULL ? -ENODEV : 0;
}

static int af903x_tuner_attach(struct dvb_usb_adapter *adap)
{
#if LINUX_VERSION_CODE >  KERNEL_VERSION(2,6,18)
    deb_data("- Enter %s Function - chip=%d\n",__FUNCTION__, adap->id);
#else
         deb_data("- Enter %s Function - \n", __FUNCTION__);
#endif
    tuner_attach(adap->fe);
    return  0;
}

static int af903x_streaming_ctrl(struct dvb_usb_adapter *adap, int onoff)
{
#if LINUX_VERSION_CODE >  KERNEL_VERSION(2,6,18)        
    deb_data("- Enter %s Function - (%s) streaming state for chip=%d\n",__FUNCTION__, onoff?"ON":"OFF", adap->id);
    //PID off
    DL_ResetPID((BYTE)adap->id);
    PDC->fc[adap->id].bEnPID =  0;
    DL_PIDOnOff((BYTE)adap->id,0);
#else
    deb_data("- Enter %s Function - (%s) streaming state \n",__FUNCTION__, onoff?"ON":"OFF");
#endif
    
    return 0;
}

struct usb_device_id af903x_usb_id_table[] = {
        { USB_DEVICE(0x15A4,0x1000) },
        { USB_DEVICE(0x15A4,0x1001) },
        { USB_DEVICE(0x15A4,0x1002) },
        { USB_DEVICE(0x15A4,0x1003) },
        { USB_DEVICE(0x15A4,0x9035) },
        { 0},        /* Terminating entry */
};
MODULE_DEVICE_TABLE(usb, af903x_usb_id_table);

struct dvb_usb_device_properties af903x_properties[] = {
    {
        .usb_ctrl          = DEVICE_SPECIFIC,
        .download_firmware = af903x_download_firmware,
        .no_reconnect      = 1,
        .power_ctrl           = af903x_powerctrl,
        .identify_state    = af903x_identify_state,
        
#if LINUX_VERSION_CODE ==  KERNEL_VERSION(2,6,18)
        .caps = DVB_USB_HAS_PID_FILTER | DVB_USB_NEED_PID_FILTERING,
                .pid_filter_count = 32,
                .frontend_attach  = af903x_frontend_attach,
                .tuner_attach     = af903x_tuner_attach,
            .streaming_ctrl   = af903x_streaming_ctrl,
        .urb = {
            .type = DVB_USB_BULK,
            .count = 10,
            .endpoint = 0x84,
            .u = {
                .bulk = {
                    .buffersize = 65424,
                }
            }
        },    
#else
        .num_adapters = 1,
        .adapter = {
            {
                .caps = DVB_USB_ADAP_HAS_PID_FILTER | DVB_USB_ADAP_PID_FILTER_CAN_BE_TURNED_OFF,
                .pid_filter_count = 32,
                .pid_filter       = af903x_pid_filter,
                .pid_filter_ctrl  = af903x_pid_filter_ctrl,
                .frontend_attach  = af903x_frontend_attach,
                .tuner_attach     = af903x_tuner_attach,
                .streaming_ctrl   = af903x_streaming_ctrl,
                .stream = { 
                    .type = USB_BULK,
                    .count = 4,
                    .endpoint = 0x84,
                    .u = {
                        .bulk = {
                            .buffersize = 65424,
                        }
                    }
                }
            },
            {
                           .caps = DVB_USB_ADAP_HAS_PID_FILTER | DVB_USB_ADAP_PID_FILTER_CAN_BE_TURNED_OFF,
                           .pid_filter_count = 32,
                           .pid_filter       = af903x_pid_filter,
                           .pid_filter_ctrl  = af903x_pid_filter_ctrl,
                .frontend_attach  = af903x_frontend_attach,
                .tuner_attach     = af903x_tuner_attach,
                .streaming_ctrl   = af903x_streaming_ctrl,
                .stream = {
                    .type = USB_BULK,
                    .count = 4,
                    .endpoint = 0x85,
                    .u = {
                        .bulk = {
                        .buffersize = 65424,
                        }
                    }
                }
            },
        },
#endif
        .num_device_descs =1,
        .devices =  {
                        {       "ITEtech USB2.0 DVB-T Recevier",
                            { &af903x_usb_id_table[0], &af903x_usb_id_table[1],&af903x_usb_id_table[2], 
                &af903x_usb_id_table[3], &af903x_usb_id_table[4], NULL},
                                { NULL },
                        },
            {NULL},

        }
    }
};

int af903x_device_count = ARRAY_SIZE(af903x_properties);

```

---

### Post by Amraks on 2012-05-14
anyone got any suggestions?

have tried this:

sudo apt-get install libopenmpi-dev

sudo apt-get install openmpi-bin



cd ~/installer/installer/AF903x_SRC/

mpirun ./make

still no go.

---

### Post by daveb85 on 2012-05-23
[patch]("https://github.com/xgazza/DVB-AF9035_kernel-3.2.0") tested on 3.2.0-24 with kaffeine.

---

### Post by Amraks on 2012-05-24
This what I get I'm using the blazetv stick

[http://linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick](http://linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick)

af9035: tuner ID:40 not supported, please report!

```
[ 1154.629959] IR NEC protocol handler initialized
[ 1154.631583] IR RC5(x) protocol handler initialized
[ 1154.633968] IR RC6 protocol handler initialized
[ 1154.634199] af9035: tuner ID:40 not supported, please report!
[ 1154.634473] usbcore: registered new interface driver dvb_usb_af9035
[ 1154.636945] IR JVC protocol handler initialized
[ 1154.638910] IR Sony protocol handler initialized
[ 1154.640606] IR MCE Keyboard/mouse protocol handler initialized
[ 1154.642722] lirc_dev: IR Remote Control driver registered, major 250 
[ 1154.642948] IR LIRC bridge handler initialized
[ 1357.462658] usb 1-2: USB disconnect, device number 6
[ 1359.040037] usb 1-2: new high-speed USB device number 7 using ehci_hcd
[ 1359.182906] af9035: tuner ID:40 not supported, please report!
[ 1359.187239] input: Afa Technologies Inc. AF9035A USB Device as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.1/input/input6
[ 1359.187485] generic-usb 0003:15A4:1001.0005: input,hidraw0: USB HID v1.01 Keyboard [Afa Technologies Inc. AF9035A USB Device] on usb-0000:00:1d.7-2/input1
[ 1497.580087] usbcore: deregistering interface driver usbhid
[ 1497.745955] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input7
[ 1497.747805] generic-usb 0003:0461:4D15.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1/input0
[ 1497.776190] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input8
[ 1497.776330] generic-usb 0003:413C:2003.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.1-2/input0
[ 1497.777956] usbcore: registered new interface driver usbhid
[ 1497.777959] usbhid: USB HID core driver

```

---

### Post by Jan Alleman on 2012-07-28
With a Zolid hybrid tv stick P50659 (see [http://www.linuxtv.org/wiki/index.php/Afatech_AF9035):](http://www.linuxtv.org/wiki/index.php/Afatech_AF9035):)

tuner ID:38 not supported, please report!

Used to  work with 2.6 kernels with module source from [https://bitbucket.org/voltagex/af9035/src](https://bitbucket.org/voltagex/af9035/src), but does not compile anymore on 3.x kernels.

Found module source that compiles for 3.x kernels here: [http://openelec.tv/forum/82-dvb-tt2-support/38651-beta-driver-af9035-for-linux-32x-kernel](http://openelec.tv/forum/82-dvb-tt2-support/38651-beta-driver-af9035-for-linux-32x-kernel), with the unknown tuner id result. Source looks completely different from the source in the mercurial repository!

```
[ 5281.508164] generic-usb 0003:15A4:1003.0002: input,hidraw1: USB HID v1.01 Keyboard [Afa Technologies Inc. AF9035 USB Device] on usb-0000:00:1a.7-2/input1
[ 5281.963890] IR NEC protocol handler initialized
[ 5281.966491] IR RC5(x) protocol handler initialized
[ 5281.969048] IR RC6 protocol handler initialized
[ 5281.969658] af9035: tuner ID:38 not supported, please report!
[ 5281.969719] usbcore: registered new interface driver dvb_usb_af9035
[ 5281.971358] IR JVC protocol handler initialized
[ 5281.973709] IR Sony protocol handler initialized
[ 5281.975772] IR MCE Keyboard/mouse protocol handler initialized
[ 5281.978227] lirc_dev: IR Remote Control driver registered, major 249 
[ 5281.978495] IR LIRC bridge handler initialized
```

---

### Post by ivanohe on 2012-10-07
For kernel 3.2 you should use [https://github.com/xgazza/DVB-AF9035_kernel-3.2.0](https://github.com/xgazza/DVB-AF9035_kernel-3.2.0), but I did not succeed in getting the IR receiver recognized on my raspberry pi.

---

