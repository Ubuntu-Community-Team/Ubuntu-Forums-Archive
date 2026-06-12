---
title: "lcd4linux.conf expressions"
date: 2014-06-18
forum: Hardware
---

### Post by diyhouse on 2014-06-18
I need some help with a formatting issue,.. I have the basic command expression as follows:-

expression a=((statfs('/', 'bfree')*statfs('/', 'bsize'))/1024/1024);b=((statfs('/mnt/Raspi', 'bfree')*statfs('/mnt/Raspi', 'bsize'))/1024/1024)

which displays the number of free blocks on a designated file system,.. but I would prefer/like to simply show the number of free gigabytes with a preceding label

eg (sda)23.1G,.. or (sdb)3234.4G or (sdc)0.1G

My understanding of the expression format is limited to examples I have found and I have not found anything relating as far as I can see. ( BTW why does the expression start "a=",.. I do not understand this bit either ).

can anyone help me?

many thanks

---

### Post by diyhouse on 2014-09-04
After some further investigation and some playing,.. I found a way of displaying what I wanted,..

However it was at this point I ran into an lcd4linux ( and many other programs limit ), that any line processed must be less than 256 characters...
Not wishing to be defeated I then adopted another approach and decided to show free space as a percentage, this is because it is much more compact and does not rely on the observer knowing how much base memory is really installed.

So the widget to display percentage free space on a selected partition works out as follows:-

Widget FSSpaceRT {
    class  'Text'
    
    expression rtfr=(statfs('/', 'bfree'));rtblks=(statfs('/', 'blocks'));rt=(100-((rtfr/rtblks)*100));d='/('.floor(rt).'%)'


    prefix ''
    postfix ''
    width  7
    align  'M'
    #precision 0
    update tick
}

I use the "floor" command to truncate the result to remove the digits after the decimal place,...    87.3% or 87.5% was neither here or there, 87% was just fine as an indicator of usage...


also found that lcd4linux -i could be used to test expressions,.. very useful for debugging....

My finished file for my GLCD2USB is attached with a txt extension...

---

