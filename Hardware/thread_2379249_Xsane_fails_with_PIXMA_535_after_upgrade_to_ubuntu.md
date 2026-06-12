---
title: "Xsane fails with PIXMA 535 after upgrade to ubuntu 17.10"
date: 2017-12-03
forum: Hardware
---

### Post by axe87 on 2017-12-03
Having just upgraded to 17.10 Xsane fails with "Error during read: Error during device I/O". Previously, I'd had a problem with Xsane after migrating to 64 bit ubuntu. This was [fixed]("https://ubuntuforums.org/showthread.php?t=2353118"). The error I get this time is different and Canon scangearmp works fine. Also, I see that libsane is now libsane1 and updated to 1.0.27-1~experimental2ubuntu2. Therefore I'm not sure if the original fix will work or indeed how to install as Xsane is now dependent on libsane1.

With SANE_DEBUG_PIXMA=3 the error the log gives me

```
 $ xsane
[sanei_debug] Setting debug level of pixma to 3.
[pixma] pixma is compiled with pthread support.
[pixma] pixma version 0.17.37
[pixma] Scanner model found: Name MX530(Canon PIXMA MX530 Series) matches MX530 series
[pixma] pixma_collect_devices() found Canon PIXMA MX530 Series at bjnp://192.168.2.113:8612/timeout=1000
[pixma] pixma_find_scanners() found 1 devices
[pixma] Scanner model found: Name MX530(Canon PIXMA MX530 Series) matches MX530 series
[pixma] pixma_collect_devices() found Canon PIXMA MX530 Series at bjnp://192.168.2.113:8612/timeout=1000
[pixma] pixma_open(): Canon PIXMA MX530 Series
[pixma] *mp150_open***** This is a generation 4 scanner.  *****
[pixma] Reader task started
[pixma] Reader task id=140166169151232 (threaded)
[pixma] Setting non-blocking mode
[pixma] 
[pixma] pixma_scan(): start
[pixma]   line_size=1914 image_size=1678578 channels=3 depth=8
[pixma]   dpi=75x75 offset=(0,0) dimension=638x877
[pixma]   gamma_table=0x5597e2177b48 source=0
[pixma]   threshold=127 threshold_curve=0
[pixma]   adf-wait=0
[pixma]   ADF page count: 0
[bjnp] bjnp_recv_header: ERROR - could not read response header (select timed out after 1000 ms)!
[pixma] No response yet. Timed out in 8 sec.
[bjnp] bjnp_recv_header: ERROR - Received response has serial 9, expected 10
[pixma] No response yet. Timed out in 7 sec.
[bjnp] bjnp_recv_header: ERROR - Received response has serial 29299, expected 11
[pixma] No response yet. Timed out in 6 sec.
[bjnp] bjnp_recv_header: ERROR - Received response has cmd code 110, expected 32
[pixma] No response yet. Timed out in 5 sec.
[bjnp] bjnp_recv_header: ERROR - Received response has cmd code 63, expected 32
[pixma] No response yet. Timed out in 4 sec.
[bjnp] bjnp_recv_header: ERROR - Received response has cmd code 118, expected 32
[pixma] No response yet. Timed out in 3 sec.
[bjnp] bjnp_recv_header: ERROR - Received response has cmd code 99, expected 32
[pixma] No response yet. Timed out in 2 sec.
[bjnp] bjnp_recv_header: ERROR - Received response has cmd code 47, expected 32
[pixma] No response yet. Timed out in 1 sec.
[pixma] WARNING: Error in response phase. cmd:3c3f
[pixma]   If the scanner hangs, reset it and/or unplug the USB cable.
[bjnp] bjnp_recv_header: ERROR - Received response has cmd code 34, expected 33
[bjnp] sanei_bjnp_write_bulk: ERROR - Could not read response to command!
[bjnp] bjnp_recv_header: ERROR - Received response has cmd code 110, expected 33
[bjnp] sanei_bjnp_write_bulk: ERROR - Could not read response to command!
[pixma] Scanner hangs? Sending abort_session command.
[bjnp] bjnp_recv_header: ERROR - Received response has cmd code 101, expected 32
[bjnp] bjnp_recv_header: ERROR - Received response has cmd code 82, expected 33
[bjnp] sanei_bjnp_write_bulk: ERROR - Could not read response to command!
[bjnp] bjnp_recv_header: ERROR - Received response has cmd code 112, expected 33
[bjnp] sanei_bjnp_write_bulk: ERROR - Could not read response to command!
[bjnp] bjnp_recv_header: ERROR - Received response has cmd code 101, expected 33
[bjnp] sanei_bjnp_write_bulk: ERROR - Could not read response to command!
[pixma] WARNING:abort_session() failed -9
[bjnp] bjnp_recv_header: ERROR - Received response has cmd code 118, expected 33
[bjnp] sanei_bjnp_write_bulk: ERROR - Could not read response to command!
[pixma] pixma_scan() failed ETIMEDOUT
[pixma] Reader task terminated: ETIMEDOUT
[pixma] read_image():reader task closed the pipe:0 bytes received, 1678578 bytes expected

```

---

