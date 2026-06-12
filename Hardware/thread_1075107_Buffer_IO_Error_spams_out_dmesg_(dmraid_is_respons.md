---
title: "Buffer IO Error spams out dmesg (dmraid is responsible)"
date: 2009-02-19
forum: Hardware
---

### Post by vertago1 on 2009-02-19
I have a dmraid array for my /home folder and would like to get rid of some errors that are plaguing both the system startup and dmesg. Here is an excerpt

[   16.029597] sda: rw=0, want=1562915761, limit=976773168                                                                         
[   16.029598] attempt to access beyond end of device                                                                              
[   16.029600] sda: rw=0, want=1562915762, limit=976773168                                                                         
[   16.029601] attempt to access beyond end of device                                                                              
[   16.029602] sda: rw=0, want=1562915763, limit=976773168                                                                         
[   16.029604] attempt to access beyond end of device                                                                              
[   16.029605] sda: rw=0, want=1562915764, limit=976773168                                                                         
[   16.029607] attempt to access beyond end of device                                                                              
[   16.029608] sda: rw=0, want=1562915765, limit=976773168                                                                         
[   16.029609] attempt to access beyond end of device                                                                              
[   16.029611] sda: rw=0, want=1562915766, limit=976773168                                                                         
[   16.029612] attempt to access beyond end of device                                                                              
[   16.029613] sda: rw=0, want=1562915767, limit=976773168                                                                         
[   16.029616] attempt to access beyond end of device                                                                              
[   16.029617] sda: rw=0, want=1562915768, limit=976773168                                                                         
[   16.029619] attempt to access beyond end of device                                                                              
[   16.029620] sda: rw=0, want=1562915769, limit=976773168                                                                         
[   16.029621] attempt to access beyond end of device                                                                              
[   16.029623] sda: rw=0, want=1562915770, limit=976773168                                                                         
[   16.029624] attempt to access beyond end of device                                                                              
[   16.029625] sda: rw=0, want=1562915771, limit=976773168                                                                         
[   16.029627] attempt to access beyond end of device                                                                              
[   16.029628] sda: rw=0, want=1562915772, limit=976773168                                                                         
[   16.029630] attempt to access beyond end of device                                                                              
[   16.029631] sda: rw=0, want=1562915773, limit=976773168                                                                         
[   16.029633] attempt to access beyond end of device                                                                              
[   16.029634] sda: rw=0, want=1562915774, limit=976773168                                                                         
[   16.029635] attempt to access beyond end of device                                                                              
[   16.029637] sda: rw=0, want=1562915775, limit=976773168                                                                         
[   16.029639] attempt to access beyond end of device                                                                              
[   16.029640] sda: rw=0, want=1562915776, limit=976773168                                                                         
[   16.029642] attempt to access beyond end of device                                                                              
[   16.029643] sda: rw=0, want=1562915777, limit=976773168                                                                         
[   16.029645] attempt to access beyond end of device                                                                              
[   16.029646] sda: rw=0, want=1562915778, limit=976773168                                                                         
[   16.029647] attempt to access beyond end of device                                                                              
[   16.029649] sda: rw=0, want=1562915779, limit=976773168

I followed the instructions at this site: [http://le-gall.net/sylvain+violaine/blog/index.php?2007/12/04/32-solving-the-dmraid-and-attempt-to-access-beyond-end-of-device-problem](http://le-gall.net/sylvain+violaine/blog/index.php?2007/12/04/32-solving-the-dmraid-and-attempt-to-access-beyond-end-of-device-problem)

but I am still having the same problem. Please help!

---

