---
title: "Hardy doesn't always shut down completely"
date: 2008-05-07
forum: Hardware
---

### Post by notesetter on 2008-05-07
Hello,

Sometimes when I shut down my Compaq Presario Laptop (It doesn't hibernate or suspend) it goes through its shutdown routine, the "closing" splash screen acts as expected, and then I get this message or something like it:

NetworkManager: <WARN> nm_signal_handler(): Caught signal 15, shutting down normally.

NetworkManager: <info> Cuaght termination signal

NetworkManager: <debug> [1210108670.020308] nm_print_open_socks(): Open Sockets List:

NetworkManager: <debug> [1210108670.021162] nm_print_open_socks(): Open Sockets List Done

NetworkManager: <WARN> nm_dbus_init(): nm_dbus_init() could not get the system bus. Make sure the message bus daemon is running!

It doesn't go further than this. It usually ends with me unplugging the power cord and then popping out the battery.

Anyone want to take a crack at it?

It may be worth noting that it's a dual-boot system running Windows XP home on a primary partition.

Thanks,

Dave

---

### Post by shirokurokun on 2008-05-07
I might have the same problem. It never shuts down properly(?). It just stops at xubuntu loading screen.

---

### Post by jschwartz73 on 2008-05-27
I'm having the same problem.  My Lenovo ThinkPad T61P freezes on shutdown, the last item on the screen is:

NetworkManager: <info> Deactivating device eth0.

Any thoughts?

---

### Post by jschwartz73 on 2008-05-27
A little more information, my /var/log/messages file contains 12 hours of:
May 27 21:04:49 jschwartz-laptop kernel: [ 7200.201817] DEV_NAME: Name of device passed is: eth1
May 27 21:04:49 jschwartz-laptop kernel: [ 7201.028589] DEV_IFINDEX: Index is : 4
May 27 21:04:49 jschwartz-laptop kernel: [ 7201.028597] DEV_IFINDEX: Index is : 4
May 27 21:04:49 jschwartz-laptop kernel: [ 7201.028600] DEV_IFINDEX: Index is : 4
May 27 21:04:49 jschwartz-laptop kernel: [ 7201.028603] DEV_IFINDEX: Index is : 4
May 27 21:04:49 jschwartz-laptop kernel: [ 7201.028606] DEV_NAME: Name of device passed is: eth1
May 27 21:04:49 jschwartz-laptop kernel: [ 7201.028632] DEV_IFINDEX: Index is : 4
May 27 21:04:49 jschwartz-laptop kernel: [ 7201.028635] DEV_IFINDEX: Index is : 4
May 27 21:04:49 jschwartz-laptop kernel: [ 7201.028638] DEV_IFINDEX: Index is : 4
May 27 21:04:49 jschwartz-laptop kernel: [ 7201.028641] DEV_IFINDEX: Index is : 4
May 27 21:04:52 jschwartz-laptop kernel: [ 7201.028644] DEV_NAME: Name of device passed is: eth1
May 27 21:04:52 jschwartz-laptop kernel: [ 7201.353643] DEV_IFINDEX: Index is : 2
May 27 21:04:52 jschwartz-laptop kernel: [ 7201.353651] DEV_IFINDEX: Index is : 2
May 27 21:04:52 jschwartz-laptop kernel: [ 7201.353655] DEV_NAME: Name of device passed is: eth0
May 27 21:04:52 jschwartz-laptop kernel: [ 7201.353683] DEV_IFINDEX: Index is : 2
May 27 21:04:52 jschwartz-laptop kernel: [ 7201.353686] DEV_IFINDEX: Index is : 2
May 27 21:04:55 jschwartz-laptop kernel: [ 7201.353689] DEV_NAME: Name of device passed is: eth0
May 27 21:04:55 jschwartz-laptop kernel: [ 7201.843070] DEV_IFINDEX: Index is : 4
May 27 21:04:55 jschwartz-laptop kernel: [ 7201.843079] DEV_IFINDEX: Index is : 4
May 27 21:04:55 jschwartz-laptop kernel: [ 7201.843082] DEV_IFINDEX: Index is : 4
May 27 21:04:55 jschwartz-laptop kernel: [ 7201.843085] DEV_IFINDEX: Index is : 4
May 27 21:04:55 jschwartz-laptop kernel: [ 7201.843088] DEV_NAME: Name of device passed is: eth1
May 27 21:04:55 jschwartz-laptop kernel: [ 7201.848648] DEV_IFINDEX: Index is : 4
May 27 21:04:55 jschwartz-laptop kernel: [ 7201.848655] DEV_IFINDEX: Index is : 4
May 27 21:04:55 jschwartz-laptop kernel: [ 7201.848658] DEV_IFINDEX: Index is : 4
May 27 21:04:55 jschwartz-laptop kernel: [ 7201.848661] DEV_IFINDEX: Index is : 4
May 27 21:04:57 jschwartz-laptop kernel: [ 7201.848664] DEV_NAME: Name of device passed is: eth1
May 27 21:04:57 jschwartz-laptop kernel: [ 7201.963352] DEV_IFINDEX: Index is : 4
May 27 21:04:57 jschwartz-laptop kernel: [ 7201.963362] DEV_IFINDEX: Index is : 4
May 27 21:04:57 jschwartz-laptop kernel: [ 7201.963365] DEV_IFINDEX: Index is : 4
May 27 21:04:57 jschwartz-laptop kernel: [ 7201.963369] DEV_IFINDEX: Index is : 4
May 27 21:04:57 jschwartz-laptop kernel: [ 7201.963373] DEV_NAME: Name of device passed is: eth1
May 27 21:04:57 jschwartz-laptop kernel: [ 7201.963580] DEV_IFINDEX: Index is : 4
May 27 21:04:57 jschwartz-laptop kernel: [ 7201.963584] DEV_IFINDEX: Index is : 4
May 27 21:04:57 jschwartz-laptop kernel: [ 7201.963587] DEV_IFINDEX: Index is : 4
May 27 21:04:57 jschwartz-laptop kernel: [ 7201.963590] DEV_IFINDEX: Index is : 4

---

### Post by Ericwt on 2008-05-27
I have the same problem eith Toshiba A45 s2501 laptop on 8.04
Will shut down sometimes sometimes on shutdown the fan will come on and I get a black screen. I have to shut down holding power button. This was not the case with 7.10
Any help would be great
Eric

---

### Post by ppl on 2008-06-13
> **Ericwt said:**
> I have the same problem eith Toshiba A45 s2501 laptop on 8.04
Will shut down sometimes sometimes on shutdown the fan will come on and I get a black screen. I have to shut down holding power button. This was not the case with 7.10
Any help would be great
Eric

I have exactly same problem with a Thinkpad R32. I haven't get a chance try the solution here: [http://ubuntuforums.org/showthread.php?t=396418]("http://ubuntuforums.org/showthread.php?t=396418")
Only one line need to add, worth trying:).

edit: That solution doesn't seems work for me, however I get it solved by turn "wake on LAN" options off in my laptop bios. It is still possible that solution plus correct setting in bios together work for me, so it is still worth doing that solution from that link

---

