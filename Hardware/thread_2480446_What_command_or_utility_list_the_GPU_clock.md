---
title: "What command or utility list the GPU clock ?"
date: 2022-10-30
forum: Hardware
---

### Post by aug7744 on 2022-10-30
Hello.
I only want see what is the IGP clock used at idle moment.
IGP is Radeon HD 3000.

Have any command line or tool does show the IGP and GPU clock ?

Thanks for reading.

---

### Post by mIk3_08 on 2022-10-31
If you want to display the information of your gpu here is the command  below. But if you want to monitor your cpu state Ubuntu has system  monitor and you can also add some application that has a system  monitoring that can be displayed on you desktop. maybe conky  and etc. Regards and cheers.
```
sudo lshw -C display
```

---

### Post by aug7744 on 2022-11-01
Thanks.
Doing the command is listed
clock 33 Mhz ... however the IGP is 350 MHZ. Thus I not understand if the command is doing an wrong value or if IGP is using an idle power mode.

---

### Post by mIk3_08 on 2022-11-02
if you want a monitoring tool application for your gpu you can use conky. Regards and cheers

---

### Post by aug7744 on 2022-11-27
Thanks for your reply.

---

