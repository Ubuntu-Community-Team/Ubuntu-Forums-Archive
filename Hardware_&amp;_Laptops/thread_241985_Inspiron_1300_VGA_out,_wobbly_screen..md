---
title: "Inspiron 1300: VGA out, wobbly screen."
date: 2006-08-23
forum: Hardware &amp; Laptops
---

### Post by Porch on 2006-08-23
Graphics are Intel 945 something and everything works great with the 915resulation patch. 

But the VGA out looks strange when I hit the hot key. 
Just having VGA out and LCD off, any monitor I plug into it says "out of range". 

If I try to do both LCD and external monitor (I have tried a few), then the LCD looks fine, but the external monitor has a wobble in it. I am not sure what to call it and I can't take a screen shot of it. 

```

Section "Monitor"                                                                                                                                         
        Identifier      "Generic Monitor"                                                                                                                 
        Option          "DPMS"                                                                                                                            
        HorizSync       28-60                                                                                                                             
        VertRefresh     43-60                                                                                                                             
                                                                                                                                                                                                                                                                                                        EndSection 


```

I don't think the Vert refresh rate is too high. 

What am I missing? 

Thanks
Porch

---

