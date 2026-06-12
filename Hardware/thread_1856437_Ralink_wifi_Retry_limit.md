---
title: "Ralink wifi Retry limit"
date: 2011-10-08
forum: Hardware
---

### Post by raad qandah on 2011-10-08
Hi all,
I have a Cisco WUSB600N V2 with Ralink 3572 as the chipset
I have downloaded the driver (2011_0427_RT3572_Linux_STA_v2.5.0.0) from ralink official site 
and I need for my project to find the place in the driver code where the retry limit is increased after a data packet drop 
and I've found this:

do
        {
            if (RTMP_TEST_FLAG(pAd, fRTMP_ADAPTER_NIC_NOT_EXIST))                
                return;
            /* Write 0x90 to BBP_R25 to transmit test tone*/
            RTMP_BBP_IO_WRITE8_BY_REG_ID(pAd, BBP_R25, 0x90);

            RTMPusecDelay(1000);
            /* Read BBP_R55[6:0] for received power, set R55x = BBP_R55[6:0]*/
            RTMP_BBP_IO_READ8_BY_REG_ID(pAd, BBP_R55, &value);
            R55x = value & 0xFF;

        } while ((ReTry++ < 100) && (R55x == 0));

in the file rt30xx.c in the directory chips but I am not sure if this is really what I want so can anyone confirm it to me?

please help I am very new to drivers
Thanks in advance

---

