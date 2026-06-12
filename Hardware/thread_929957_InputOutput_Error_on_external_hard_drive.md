---
title: "Input/Output Error on external hard drive"
date: 2008-09-25
forum: Hardware
---

### Post by Ezetreal on 2008-09-25
Hello

I have been having this Input/Output error with my hard drive for a while and I can't figure out whether it is the drive itself i should be worried about.

I tried every kind of test i could find on this forum to see whether it had bad sectors and everything came back negative.

Every once in a while (today i was copying multiple big files, movies, at the same time) i get this error and i need to unmount and remount the drive and it works well again, meaning i can copy the same files back with no error and can access the folders on the drive without this error (before the remount it wouldn't allow me to access the folder i was copying to (not sure about the other folders actually).

If anyone can enlighten me on this i would appreciate it very much. I don't want to get rid of a good hard drive if the problem isn't from it.

Thank you very much

---

### Post by prshah on 2008-09-25
> **Ezetreal said:**
> 
Every once in a while (today i was copying multiple big files, movies, at the same time) i get this error and i need to unmount and remount the drive and it works well again, meaning i can copy the same files back with no error and can access the folders on the drive without this error


I suggest you check the power supply to the drive; if it is faulty or delivering a lower voltage, then that could cause such a problem. To check the power, get a (cheap) digital multimeter, dial the selector to DC 20v and stick one pin into the center (hole) and the other pin on the outer part (metal) of the pin. The display should give you the active voltage. Hold it for a few seconds (10~20) to see if it's steady.

Be careful not to accidentally short the connector (by touching the multimeter leads together) !

---

### Post by Ezetreal on 2008-09-25
Thanks,  

Although I don't think that is it, it is a new external drive case, I'll have to go buy a multimeter and try that.

---

### Post by prshah on 2008-09-26
> **Ezetreal said:**
> 
Although I don't think that is it, it is a new external drive case, I'll have to go buy a multimeter and try that.

If it's a new one, I think you're right, that cannot be the problem; how about checking the message log for suspicious entries? System-Administration-System Log.

Also, from a terminal (Applications-Accessories-Terminal), please post the output of the commands below:```
dmesg | grep -i -E drdy\|error\|seek
```

---

### Post by Ezetreal on 2008-09-26
This is the output of the command. However, the drive in question is not plugged in at the moment. I don't know what the command does so i don't know if that's important. 
Do you need this output right after the error occurs ?

~$ dmesg | grep -i -E drdy\|error\|seek
[   10.518033] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

Thanks for taking the time to help me out.

---

### Post by anorexicpillow on 2008-10-01
When I go to open my External HD it says "The folder contents could not be displayed. Sorry, couldn't display all the contents of "Simple Drive": Input/Output error" and when I run the command you suggested it said "Buffer I/O error on device sdb1, logical block 786433" Any Ideas on how to fix this? All of my media is on there.

---

