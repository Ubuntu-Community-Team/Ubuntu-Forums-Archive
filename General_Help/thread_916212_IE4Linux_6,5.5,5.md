---
title: "IE4Linux 6,5.5,5"
date: 2008-09-10
forum: General Help
---

### Post by MKep on 2008-09-10
Okay, quick question.  I am having a problem with Internet Explorer 4 Linux.  Once I turn my computer on, IE4Linux will only open once.  If I close it and try to reopen it -- nothing.  I have to restart the computer if I want to open it again.

Any ideas?:confused:

---

### Post by russlar on 2008-09-10
Firefox.

---

### Post by kokkus on 2008-09-10
Hehe yes use firefox LOL
But ok, it goes to the system trey. Check your panel.

---

### Post by Crafty Kisses on 2008-09-10
Try running it in Terminal, do you get any errors?

---

### Post by LingLing1337 on 2008-09-10
> **MKep said:**
> Okay, quick question.  I am having a problem with Internet Explorer 4 Linux.  Once I turn my computer on, IE4Linux will only open once.  If I close it and try to reopen it -- nothing.  I have to restart the computer if I want to open it again.

Any ideas?:confused:

Why in the world would you be using IE? Get Firefox 3 or Swiftfox.

---

### Post by kokkus on 2008-09-10
Epiphany looks like IE If that's the reason y u use it.
You can also use galaxy.

But check your panel if u have a ie logo there when u close it.
If not, add IE to your panel and try again.
If this doesn't work, ditch IE and choose another browser :)

---

### Post by MKep on 2008-09-10
Trust me, I use Firefox typically.  I really don't like IE.  But I am taking a class at a community college that uses this very minimalist version of Blackboard and I can only view it with IE.  I emailed the Web Director and asked why they can't be more proactive in 2008, and he said that there is an upgrade that would fix the problem (the problem of the program only being visible in IE), but the school can't afford it.

---

### Post by fragos on 2008-09-10
You only need run IE4Linux once which will install wine and whatever IE versons you want. For your puposes you only need IE6. IE4Linux should have created one or more links to IE in your home directory and perhaps on the desktop. Those links are what you click to run IE.

---

### Post by shae on 2008-09-11
The problem from what I can tell is that IE does not cleanly close in linux.  Sometimes it will stay open and leak memory.  You should use killall NAME_OF_PROCESS or use Gnome System Monitor to kill it.  Then you should be able to open it up again.

---

### Post by bingoUV on 2008-09-11
kill the wine processes. Search for "wine" in process name in system monitor, and kill the processes.

---

### Post by ampalaya on 2009-03-28
Hello, I am using Ubuntu for more than a year now, and it's really a great OS!!! Makes me want to trash "THAT OTHER OS" that is mostly used by the general public (lol, just kidding).

However, there are still times that i need other softwares running from different OS's. Currently I develop web applications and it is a requirement in our project that we check for compatibility. This is not by choice but of necessity. And since ie6 is one of the browsers we must check, I am rather inclined to run it on Ubuntu than using a VM or restarting my workstation just to test it on the different system.

I've been using ie4linux, and I too am encountering memory leak problems. Just the other night my machine hangs due to 100% memory usage. It's really quite irritating and still haven't found the problem why (and I'm not that too technical to even know how).

I execute the ie6 command on terminal and this is what I'm getting:
**** START ****
$ ie6 
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
err:shell:ReadCabinetState Initializing shell cabinet settings
fixme:shell:DllGetClassObject failed for CLSID=
	{53bd6b4e-3780-4693-afc3-7161c2f3ee9c} (MruLongList)
err:rebar:REBAR_WindowProc unknown msg 200b wp=00000000 lp=71180f00
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:shell:NTSHChangeNotifyRegister (0x10034,0x00008003,0x00008000,0x0000c073,0x00000001,0x32dc1c):semi stub.
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10034, wParam=0x00000000, size.cx=1440, size.cy=32000 stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_Unkwn464 hwnd=0x10038 wParam 00000001 lParam 00000000
fixme:dpa:DPA_LoadStream phDpa=0x32d658 loadProc=0x8aba1c pStream=0x141c58 lParam=141c18
fixme:dpa:DPA_LoadStream dwSize=0 dwData2=0 dwItems=0
fixme:dpa:DPA_LoadStream new hDpa=0x141c90, errorcode=80004005
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x1004e, wParam=0x00000000, size.cx=1440, size.cy=896 stub!
fixme:shell:NTSHChangeNotifyRegister (0x1004e,0x00008003,0x0c02b7ff,0x0000c073,0x00000001,0x32dc5c):semi stub.
fixme:shell:DllGetClassObject failed for CLSID=
	{871c5380-42a0-1069-a2ea-08002b30309d} (unknown)
fixme:shell:NTSHChangeNotifyRegister (0x10028,0x00008003,0x0003f5f4,0x00000410,0x00000001,0x32ea88):semi stub.
fixme:shell:SignalFileOpen (0x00000000):stub.
fixme:shell:DllGetClassObject failed for CLSID=
	{871c5380-42a0-1069-a2ea-08002b30309d} (unknown)
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x32bc78)
fixme:shell:DllGetClassObject failed for CLSID=
	{871c5380-42a0-1069-a2ea-08002b30309d} (unknown)
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:shell:DllGetClassObject failed for CLSID=
	{871c5380-42a0-1069-a2ea-08002b30309d} (unknown)
fixme:shell:DllGetClassObject failed for CLSID=
	{53bd6b4e-3780-4693-afc3-7161c2f3ee9c} (MruLongList)
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:shell:DllGetClassObject failed for CLSID=
	{53bd6b4e-3780-4693-afc3-7161c2f3ee9c} (MruLongList)
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:hook:IsWinEventHookInstalled (32773)-stub!
...
**** END ****

after that its just:
fixme:hook:IsWinEventHookInstalled (32773)-stub!
over and over, and over time my memory just peaks up.

The best solution I have so far is to just run the command on the terminal, and when my memory usage goes too high, I cancel the application by pressing CTRL+C and waits a minute 'till the memory recedes back to normal.

Hope this helps for the time being, and also hoping that someone could provide an official solution for this.

---

