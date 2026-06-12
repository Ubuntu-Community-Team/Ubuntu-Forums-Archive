---
title: "Interpreting Front End Data (Signal Strength, SNR, BER) for DVB devices"
date: 2008-06-22
forum: Hardware
---

### Post by blackhole54 on 2008-06-22
Hi All,

I hope this is the appropriate forum for this ...  I am trying to use a Hauppauge HDVR950 ATSC/NTSC USB tuner (lsusb results below). It's basically working but I am having some reception issues in ATSC mode. As I result I have been trying to look at low level data like signal strength, signal-to-noise (SNR), etc. Specifically I have been using and modifying **dtvsignal** (download:  [here]("http://pchdtv.com/downloads/dvb-atsc-tools-1.0.7.tgz")) from [pcHDTV]("http://pchdtv.com/") to extract information from the dvb front end.  Specifically this software does the following calls to pull the data:

```

        ioctl(device, FE_READ_STATUS, &status);
        ioctl(device, FE_READ_SIGNAL_STRENGTH, &snl);
        ioctl(device, FE_READ_SNR, &snr);
        ioctl(device, FE_READ_BER, &ber);
        ioctl(device, FE_READ_UNCORRECTED_BLOCKS, &uncorrected_blocks);

```I have modified the code to report the values of the last four, but now I would like to find out _exactly_ how to interpret the raw values.  I have searched the internet, including finding [this page]("http://www.linuxtv.org/docs/dvbapi/DVB_Frontend_API.html#SECTION00310000000000000000"), but I still haven't found the info I am seeking.

One possibility is that this data just doesn't follow a standard format but is vendor (and maybe model) specific. In which case, knowing that would be useful. Even more useful would be knowing where one might get the vendor specific info. However,the previously mentioned software has hints that there might actually be a standard, at least for signal strength and SNR. But the  documentation for this software is almost non-existent and I hate reading too much into the the output of these small programs. Both signal strength and SNR are returned as unsigned 16 bits. The **dtvsignal** program hints that full scale (65535) for the signal strenth is 30db, perhaps with the value being linear wrt the signal strength. Another program included (but not even mentioned in the README) is **dtvsnr**. In this case the program seems to be hinting that the SNR output is linear wrt decibels (of the ratio) and that 0 corresponds to -10 db and full scale (65535) corresponds to 40 db. But this program is even more problematic because, as I read it, it is not internally consistent. (Since it is not mentioned in the README I've wondered if maybe the program was never finished/debugged.) But taking the signal strength as linear and the SNR as decibels with the indicated scaling does seem to have some internal consistency:

The following data was taken on various channels with a modified **dtvsignal** program. The signal strength is the raw data (after smoothing) expressed as percent of full scale. The SNR (also smoothed) is raw data scaled as indicated above (0 = -10 db; FS = 40 db).

```

channel = 15 freq = 479000000Hz    SNR: -5.1   Signal:   70%   
channel = 16 freq = 485000000Hz    SNR: -4.9   Signal:   74%   
channel = 17 freq = 491000000Hz    SNR: -5.6   Signal:   64%   
channel = 18 freq = 497000000Hz    SNR: -6.1   Signal:   57%   
channel = 19 freq = 503000000Hz    SNR: -5.9   Signal:   59%   
channel = 32 freq = 581000000Hz    SNR: -5.0   Signal:   73%   
channel = 34 freq = 593000000Hz    SNR: -5.4   Signal:   66%   
channel = 38 freq = 617000000Hz    SNR: -6.6   Signal:   49%   

```If it is assumed (yes, it is an assumption that may not be true) that all channels have similar noise, then picking any pair of channels, and comparing ten times the common log of the ratio (definition of db) does in fact give aproximately the difference of the numbers reported as SNR. So this does suggest an internal consistency with the interpretation of the meaning of the raw SNR value. But if those SNR values are correctly interpreted, the values seem rather dismal, with signal buried in noise. (Which could account for my problems.)

The remaining issue is the bit error rate (BER). And maybe for me this is not an issue at all since I consistently get a value of zero. Which doesn't seem likely. Particularly considering the reception issues I have. Any thoughts on this?

I appologize for the fact that this post has been a little rambling. (Thanks for bearing with me.) I wanted to lay out what I know, what I suspect and where my thinking is on this, and this was the most orderly I could figure out to do so. Any pointers about where I might find actual documentation telling me how to interpret the raw data would be greatly appreciated. Thanks.



In case it is of any use, here is the output of **lsusb**:

```

Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 2040:6513 Hauppauge 
Bus 001 Device 001: ID 0000:0000  

```P.S.  The (GPL)  programs I mentioned above have a copyright notice for pcHDTV, but no contact info.

---

