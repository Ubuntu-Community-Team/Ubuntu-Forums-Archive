---
title: "AutoCAD Architecture 2011 w/ wine?"
date: 2010-07-28
forum: Hardware
---

### Post by carbenein on 2010-07-28
I am trying to install AutoCAD Architecture 2011 on Ubuntu 10.04 using Wine. When I try to install,  it goes smooth until it comes to the actual AutoCAD install. I attached the log file below. 

2010/6/20:13:05:42	carbentech	carbentech-r61	=== Setup started on carbentech-r61 by carbentech ===
2010/6/20:13:06:45	carbentech	carbentech-r61	=== Setup ended ===

2010/6/20:13:09:59	carbentech	carbentech-r61	=== Setup started on carbentech-r61 by carbentech ===
2010/6/20:13:10:53	carbentech	carbentech-r61	=== Setup ended ===

2010/6/20:13:10:01	carbentech	carbentech-r61	=== Setup started on carbentech-r61 by carbentech ===
2010/6/20:13:10:01	carbentech	carbentech-r61	[Error: 1060] Service does not exist
2010/6/20:13:10:01	carbentech	carbentech-r61	[Error: 6] Invalid handle
2010/6/20:13:10:01	carbentech	carbentech-r61	[Error: 6] Invalid handle
2010/6/20:13:12:44	carbentech	carbentech-r61	Install	Microsoft Visual C++ 2008 Redistributable (x86)	Succeeded	
2010/6/20:13:20:18	carbentech	carbentech-r61	Install	DirectX 9.0 Runtime	Succeeded	
2010/6/20:13:20:20	carbentech	carbentech-r61	Install	FARO LS 1.1.406.58	Succeeded	
2010/6/20:13:20:22	carbentech	carbentech-r61	Install	MSXML 6.0 Parser	Succeeded	
2010/6/20:13:20:51	carbentech	carbentech-r61	Install	Autodesk Material Library 2011	Succeeded	
2010/6/20:13:21:29	carbentech	carbentech-r61	Install	Autodesk Material Library 2011 Base Image library	Succeeded	
2010/6/20:13:22:17	carbentech	carbentech-r61	Install	AutoCAD Architecture 2011	Failed	Installation aborted, Result=120
2010/6/20:13:22:19	carbentech	carbentech-r61	Rollback	Autodesk Material Library 2011 Base Image library	Succeeded	
2010/6/20:13:22:24	carbentech	carbentech-r61	Rollback	Autodesk Material Library 2011	Succeeded	
2010/6/20:13:22:25	carbentech	carbentech-r61	Rollback	MSXML 6.0 Parser	Succeeded	
2010/6/20:13:22:26	carbentech	carbentech-r61	Rollback	FARO LS 1.1.406.58	Succeeded	
2010/6/20:13:22:27	carbentech	carbentech-r61	Rollback	DirectX 9.0 Runtime	Failed	Failure is ignored, Result=2
2010/6/20:13:22:28	carbentech	carbentech-r61	Rollback	Microsoft Visual C++ 2008 Redistributable (x86)	Failed	Installation aborted, Result=2
2010/6/21:12:26:12	carbentech	carbentech-r61	[Error: 6] Invalid handle
2010/6/21:12:26:12	carbentech	carbentech-r61	=== Setup ended ===

2010/6/22:00:13:06	carbentech	carbentech-r61	=== Setup started on carbentech-r61 by carbentech ===
2010/6/22:00:14:00	carbentech	carbentech-r61	=== Setup ended ===

2010/6/22:00:13:09	carbentech	carbentech-r61	=== Setup started on carbentech-r61 by carbentech ===
2010/6/22:00:13:09	carbentech	carbentech-r61	[Error: 1060] Service does not exist
2010/6/22:00:13:09	carbentech	carbentech-r61	[Error: 6] Invalid handle
2010/6/22:00:13:09	carbentech	carbentech-r61	[Error: 6] Invalid handle
2010/6/22:00:23:35	carbentech	carbentech-r61	Install	DirectX 9.0 Runtime	Succeeded	
2010/6/22:00:23:36	carbentech	carbentech-r61	Install	FARO LS 1.1.406.58	Succeeded	
2010/6/22:00:23:39	carbentech	carbentech-r61	Install	MSXML 6.0 Parser	Succeeded	
2010/6/22:00:23:59	carbentech	carbentech-r61	Install	Autodesk Material Library 2011	Succeeded	
2010/6/22:00:24:15	carbentech	carbentech-r61	Install	Autodesk Material Library 2011 Base Image library	Succeeded	
2010/6/22:00:25:04	carbentech	carbentech-r61	Install	AutoCAD Architecture 2011	Failed	Installation aborted, Result=120
2010/6/22:00:25:06	carbentech	carbentech-r61	Rollback	Autodesk Material Library 2011 Base Image library	Succeeded	
2010/6/22:00:25:11	carbentech	carbentech-r61	Rollback	Autodesk Material Library 2011	Succeeded	
2010/6/22:00:25:12	carbentech	carbentech-r61	Rollback	MSXML 6.0 Parser	Succeeded	
2010/6/22:00:25:13	carbentech	carbentech-r61	Rollback	FARO LS 1.1.406.58	Succeeded	
2010/6/22:00:25:14	carbentech	carbentech-r61	Rollback	DirectX 9.0 Runtime	Failed	Failure is ignored, Result=2
2010/6/22:00:25:21	carbentech	carbentech-r61	[Error: 6] Invalid handle
2010/6/22:00:25:21	carbentech	carbentech-r61	=== Setup ended ===

2010/7/28:01:51:29	carbentech	carbentech-r61	=== Setup started on carbentech-r61 by carbentech ===
2010/7/28:01:52:33	carbentech	carbentech-r61	=== Setup ended ===

2010/7/28:01:51:37	carbentech	carbentech-r61	=== Setup started on carbentech-r61 by carbentech ===
2010/7/28:01:51:37	carbentech	carbentech-r61	[Error: 1060] Service does not exist
2010/7/28:01:51:37	carbentech	carbentech-r61	[Error: 6] Invalid handle
2010/7/28:01:51:37	carbentech	carbentech-r61	[Error: 6] Invalid handle
2010/7/28:02:02:35	carbentech	carbentech-r61	Install	DirectX 9.0 Runtime	Succeeded	
2010/7/28:02:02:36	carbentech	carbentech-r61	Install	FARO LS 1.1.406.58	Succeeded	
2010/7/28:02:02:45	carbentech	carbentech-r61	Install	MSXML 6.0 Parser	Succeeded	
2010/7/28:02:03:19	carbentech	carbentech-r61	Install	Autodesk Material Library 2011	Succeeded	
2010/7/28:02:03:47	carbentech	carbentech-r61	Install	Autodesk Material Library 2011 Base Image library	Succeeded	
2010/7/28:02:04:37	carbentech	carbentech-r61	Install	AutoCAD Architecture 2011	Failed	Installation aborted, Result=120
2010/7/28:02:04:40	carbentech	carbentech-r61	Rollback	Autodesk Material Library 2011 Base Image library	Succeeded	
2010/7/28:02:04:48	carbentech	carbentech-r61	Rollback	Autodesk Material Library 2011	Succeeded	
2010/7/28:02:04:50	carbentech	carbentech-r61	Rollback	MSXML 6.0 Parser	Succeeded	
2010/7/28:02:04:52	carbentech	carbentech-r61	Rollback	FARO LS 1.1.406.58	Succeeded	
2010/7/28:02:04:54	carbentech	carbentech-r61	Rollback	DirectX 9.0 Runtime	Failed	Failure is ignored, Result=2

Any help would be much appreciated; I am an architect and would really like to run AutoCAD on Linux.

---

### Post by P4man on 2010-07-28
Its known not to work under wine, like most recent autocad releases which all depend on .net 3.5
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19791](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19791)

It should work in a VM like virtualbox, but I dont know if graphics performance would be satisfactory.

---

### Post by arjunned on 2010-07-28
Hi!

I've been breaking my head for quite a while now, as none of the newer version of Autodesk work with Wine. The only version that works well enough (for me) is AutoCAD 2004! :(
AutoCAD 2008 installs and works as well (to an extent). But the major problem is that you cant register your AutoCAD. The registration screen just comes up blank. So you have to uninstall it after the 30-day trial expires, and reinstall! (Note: When i tried 2008, i had huge problems with Layer Manager; none of the icons showed properly in the manager. Also got random freezes.)

On another note, i just came across a great CAD application called [progeSOFT 2009 Smart]("http://www.progesoft.com/en/smart-2009"). Its exactly like ACAD 2004, but it can read and write formats upto AutoCAD 2009 (which is a big plus for me). Its a windows application (only 97mb download), and works excellent with Wine! Been using it for a while now, and its running smooth.

Hope this helps.
Cheers!

---

