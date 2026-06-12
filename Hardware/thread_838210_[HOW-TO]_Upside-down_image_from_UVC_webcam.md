---
title: "[HOW-TO] Upside-down image from UVC webcam"
date: 2008-06-23
forum: Hardware
---

### Post by arjos85 on 2008-06-23
[FONT=Arial][SIZE=2]Hi everybody,
it's a very quick how-to that will help you to solve the problem of those webcams who give back upside-down images/videos!!!
This help is intended only for those who have a UVC capable webcam.
But it will be usefull only if your webcam supports YUV image format and the applications that use your webcam request YUV format to your webcam!!! I've tested it and it works with:
skype, amsn, kopete, luvcview, mplayer!!

So...let's start!!!!

In order to know if your webcam is UVC capable you just need to open your shell and run:
[/SIZE][/FONT][SIZE=2]```
lsusb
```[/SIZE][FONT=Arial][SIZE=2]
you will get something like this:
> Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID xxxx:yyyy "Your_Webcam_Model"
Bus 001 Device 001: ID 0000:0000Then type:
[/SIZE][/FONT][SIZE=2]```
sudo lsusb -d xxxx:yyyy -v | grep "14 Video"
```[/SIZE][FONT=Arial][SIZE=2]
If you get something like the following, your webcam is UVC capable:
[/SIZE][/FONT][SIZE=2]>       bFunctionClass         14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
[/SIZE][FONT=Arial][SIZE=2]
If your webcam passes this test, you can go on reading. Otherwise, your camera needs to use propertary driver, because it doesn't use standard protocol/command.

Well,
now you need to donwload the UVCVIDEO driver sources, but they are on a SVN repository, so you need to install the SVN client:
[/SIZE][/FONT][SIZE=2]```
sudo apt-get install subversion
```[/SIZE][FONT=Arial][SIZE=2]and now you can download the sources:
[/SIZE][/FONT][SIZE=2]```
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
```[/SIZE][FONT=Arial][SIZE=2]
The sources will be saved into a folder called "Trunk" in the path from where you run the previous command.

Now there are 2 solutions, please try both and tell me which one you think is the  best!!

[B][COLOR=Red]Now for both solutions there are two patches: the former gives back mirrored images, the latter NOT mirrored images.
[/COLOR][COLOR=Red]You have to copy one of them into "Trunk" folder in a file (called for example "uvc_video_solution1.patch"), and then from terminal go into the "Trunk" folder and do:
[/COLOR][/B][/SIZE][/FONT][SIZE=2]**[COLOR=Red]```
patch < uvc_video_solution1.patch
```WARNING: each of the following patch refers to the original "uvc_video.c" file, so before applying a new patch be sure that the "uvc_video.c" file[/COLOR]**[/SIZE][SIZE=2]**[COLOR=Red] in "Trunk" folder[/COLOR]**[/SIZE][SIZE=2][B][COLOR=Red] is the original one. So please remember to backup the original file.
[/COLOR][/B][/SIZE] [FONT=Arial][COLOR=Red][SIZE=2] 
[B]_WARNING:_
YOU HAVE TO ADD A BLANK LINE AT THE END OF EACH PATCH IN ORDER TO SUCCEED THE PATCHING!!

[U]NEWS:
[/U]NOW YOU CAN DOWNLOAD THE PATCHES AND DON'T NEED ANY MORE TO ADD A NEW LINE!!!
TAKE A LOOK AT THE BOTTOM OF THIS HOW-TO, YOU WILL FIND 4 PATCHES, JUST CHOOSE THE ONE YOU PREFER AND DONWLOAD IT!![/B]   ;)

_[COLOR=Blue]**WARNING: Patches available in this HowTo refer to the UVC driver version 0.1.0, so if you install a different version you will have to apply the patch by hand!!!**[/COLOR]_

**_FIRST SOLUTION (MIRRORED IMAGES)_**
[/SIZE][/COLOR][/FONT][FONT=Arial][SIZE=2][COLOR=Red]# modified June 26, 2008[/COLOR]
[/SIZE][/FONT]```
diff -uN UVCVIDEO_v0.1.0/uvc_video.c UVCVIDEO_patched/uvc_video.c
--- UVCVIDEO_v0.1.0/uvc_video.c    2008-06-26 10:41:01.000000000 +0200
+++ UVCVIDEO_patched/uvc_video.c    2008-06-26 15:33:33.000000000 +0200
@@ -371,23 +371,92 @@
     return data[0];
 }
 
+/* This patched function allows to overturn video images from an upside-down
+ * orientation to a normal one with mirrored effect. The conversion simply
+ * consists in reversing the order of the rows of imagines.
+ * This patch performs its job just once for each frame and only when current
+ * frame is completed, but each time it is required to allocate memory in order
+ * to store a copy of that frame.
+ * This patch should work with all YUV image formats.
+ */
 static void uvc_video_decode_data(struct uvc_video_device *video,
         struct uvc_buffer *buf, const __u8 *data, int len)
 {
     struct uvc_video_queue *queue = &video->queue;
     unsigned int maxlen, nbytes;
     void *mem;
+    /* Patch variables */
+    __u8 *mem_tmp, *ptr_tmp;
+    int i, k, row_size;
 
     if (len <= 0)
         return;
 
     /* Copy the video data to the buffer. */
+    /* How many bytes are needed to complete the buffer? */
     maxlen = buf->buf.length - buf->buf.bytesused;
+    /* Where do pixels stored in "data" have to be copied? */
     mem = queue->mem + buf->buf.m.offset + buf->buf.bytesused;
+    /* How many bytes really can be copied into "mem"? */
     nbytes = min((unsigned int)len, maxlen);
+    /* "nbytes" are copied from "data" to "mem" buffer.
+     * "data" stores a sequence of pixels coming from the video source.
+     * This sequence is not a full frame or a full row of pixel, but just an
+     * ordered vector of pixels (from top-left to bottom-right), whose
+     * represents just an area of the current frame.
+     * This function has to be called hundreds of times before a frame is
+     * completed and "nbytes" is not constant! Each time "data" contains the
+     * next part of the frame. At the end data stored in "mem" buffer will
+     * be used by the application who requested the video stream.
+     */
     memcpy(mem, data, nbytes);
     buf->buf.bytesused += nbytes;
 
+    /* Have the last copied bytes completed the current frame? */
+    if (nbytes == maxlen) {
+        /* Area where to save the upper half part of the original frame
+         * (just half in order to speed up the patch) before reversing.
+         */
+        mem_tmp = (__u8 *) kmalloc(buf->buf.bytesused / 2, GFP_ATOMIC);
+        if (mem_tmp != NULL ) {
+            /* Copy top-half part of frame in a temporary buffer */
+            memcpy(mem_tmp, queue->mem + buf->buf.m.offset,
+                   buf->buf.bytesused / 2);
+            /* "row_size" does not depend only on the width of the
+             * frame, but also on the pixel color depth (bpp).
+             */
+            row_size = video->streaming->cur_frame->wWidth *
+                   video->streaming->format->bpp / 8;
+            /* The following cycle just copy full frame rows from
+             * the last one stored in "mem" (and going up) to the
+             * first one (and going down) stored in "mem" itself.
+             */
+            ptr_tmp = queue->mem + buf->buf.m.offset
+                  + buf->buf.bytesused / 2;
+            /* When the top-half of the frame has been reversed,
+             * rows are copied from the last one stored in "mem_tmp"
+             * (and going up) into the bottom half part of "mem"
+             * buffer.
+             */
+            for (i = 0, k = buf->buf.bytesused / 2 - row_size;
+                 i < buf->buf.bytesused;
+                 i += row_size, k -= row_size) {
+                /* If the top-half of the frame has been
+                 * revesed, then it is needed to split the
+                 * source buffer from "mem" to "mem_tmp".
+                 */
+                if (i == buf->buf.bytesused / 2) {
+                    ptr_tmp = mem_tmp;
+                    k = buf->buf.bytesused / 2 - row_size;
+                }
+                memcpy(queue->mem + buf->buf.m.offset + i,
+                       ptr_tmp + k,
+                       row_size);
+            }
+            /* For this frame "mem_tmp" is not needed any more. */
+            kfree(mem_tmp);
+        }
+    }
     /* Complete the current frame if the buffer size was exceeded. */
     if (len > maxlen) {
         uvc_trace(UVC_TRACE_FRAME, "Frame complete (overflow).\n");


```[SIZE=4]
[/SIZE][FONT=Arial][SIZE=2][U]
[B][COLOR=Red]FIRST SOLUTION ([SIZE=5]NOT[/SIZE] MIRRORED IMAGES)
[/COLOR][/B][/U][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Red]# modified June 26, 2008[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Red]
[/COLOR][/SIZE][/FONT]```

diff -uN UVCVIDEO_v0.1.0/uvc_video.c UVCVIDEO_patched/uvc_video.c
--- UVCVIDEO_v0.1.0/uvc_video.c    2008-06-26 10:41:01.000000000 +0200
+++ UVCVIDEO_patched/uvc_video.c    2008-06-26 15:33:33.000000000 +0200
@@ -371,23 +371,105 @@
     return data[0];
 }
 
+/* This patch should work ONLY with YUY2 image formats, also known as YUYV or
+ * YUV422 formats.
+ * This patched function allows to overturn video images from an upside-down
+ * orientation to a normal one. The conversion consists in copying 4 bytes at a
+ * time (Y0,U0,Y1,V0) corresponding to 2 pixels, in a bottom-up direction, from
+ * the frame (coming from the video source) to the buffer that will be used by
+ * the application requesting the video stream. But in order to satisfy the YUY2
+ * image format byte has to be copied in this way: Y1 U0 Y0 VO.
+ * This patch performs its job just once for each frame and only when current
+ * frame is completed, but each time it is required to allocate memory in order
+ * to store a copy of that frame.
+ */
 static void uvc_video_decode_data(struct uvc_video_device *video,
         struct uvc_buffer *buf, const __u8 *data, int len)
 {
     struct uvc_video_queue *queue = &video->queue;
     unsigned int maxlen, nbytes;
     void *mem;
+    /* Patch variables */
+    __u8 *mem_tmp, *ptr_tmp;
+    int i, k, pixel_size;
 
     if (len <= 0)
         return;
 
     /* Copy the video data to the buffer. */
+    /* How many bytes are needed to complete the buffer? */
     maxlen = buf->buf.length - buf->buf.bytesused;
+    /* Where do pixels stored in "data" have to be copied? */
     mem = queue->mem + buf->buf.m.offset + buf->buf.bytesused;
+    /* How many bytes really can be copied into "mem"? */
     nbytes = min((unsigned int)len, maxlen);
+    /* "nbytes" are copied from "data" to "mem" buffer.
+     * "data" stores a sequence of pixels coming from the video source.
+     * This sequence is not a full frame or a full  row of pixel, but just
+     * an ordered vector of pixels (from top-left to bottom-right), whose
+     * represents just an area of the current frame.
+     * This function has to be called hundreds of times before a frame is
+     * completed and "nbytes" is not constant! Each time "data" contains the
+     * next part of the frame. At the end data stored in "mem" buffer will
+     * be used by the application who requested the video stream.
+     */
     memcpy(mem, data, nbytes);
     buf->buf.bytesused += nbytes;
 
+    /* Have the last copied bytes completed the current frame? */
+    if (nbytes == maxlen) {
+        /* Area where to save the original frame before manipulation. */
+        mem_tmp = (__u8 *) kmalloc(buf->buf.bytesused / 2, GFP_ATOMIC);
+        if (mem_tmp != NULL ) {
+            /* Copy the original frame in a temporary buffer. */
+            memcpy(mem_tmp, queue->mem + buf->buf.m.offset,
+                   buf->buf.bytesused / 2);
+            /* "pixel_size" depens on the pixel color depth (bpp),
+             * but in YUY2 image format is constant and equal to 2.
+             */
+             pixel_size = video->streaming->format->bpp / 8;
+            /* The following loop copy 2 pixels at a time (4 bytes
+             * in YUY2 format) from the last two stored in "mem"
+             * (and going back) to the first two (and going on)
+             * stored in "mem" itself following a sort of YUY2
+             * algorithm.
+             */
+            ptr_tmp = queue->mem + buf->buf.m.offset
+                  + buf->buf.bytesused / 2;
+            /* When the top-half of the frame has been reversed,
+             * rows are copied from the last one stored in "mem_tmp"
+             * (and going up) into the bottom half part of "mem"
+             * buffer.
+             */
+            for (i = 0, k = buf->buf.bytesused / 2 - 2 * pixel_size;
+                 i < buf->buf.bytesused;
+                 i += 2 * pixel_size, k -= 2 * pixel_size){
+                /* If the top-half of the frame has been
+                 * revesed, then it is needed to split the
+                 * source buffer from "mem" to "mem_tmp".
+                 */
+                if (i == buf->buf.bytesused / 2) {
+                    ptr_tmp = mem_tmp;
+                    k = buf->buf.bytesused / 2
+                        - 2 * pixel_size;
+                }
+                 /* The order of copied bytes is changed from
+                  * (Y0 U0 Y1 V1) to (Y1 U0 Y0 V1), i.e. from
+                  * (#0 #1 #2 #3) to (#2 #1 #0 #3).
+                  */
+                 ((__u8 *)(queue->mem+buf->buf.m.offset + i))[0] =
+                 ((__u8 *)(ptr_tmp + k))[2];
+                 ((__u8 *)(queue->mem+buf->buf.m.offset + i))[1] =
+                 ((__u8 *)(ptr_tmp + k))[1];
+                 ((__u8 *)(queue->mem+buf->buf.m.offset + i))[2] =
+                 ((__u8 *)(ptr_tmp + k))[0];
+                 ((__u8 *)(queue->mem+buf->buf.m.offset + i))[3] =
+                 ((__u8 *)(ptr_tmp + k))[3];
+            }
+            /* For this frame "mem_tmp" is not needed any more. */
+            kfree(mem_tmp);
+        }
+    }
     /* Complete the current frame if the buffer size was exceeded. */
     if (len > maxlen) {
         uvc_trace(UVC_TRACE_FRAME, "Frame complete (overflow).\n");



```[FONT=Arial][SIZE=2][U][COLOR=Red][B]
SECOND SOLUTION (MIRRORED IMAGES)[/B][/COLOR][/U]
[/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Red]# modified June 26, 2008[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Red]
[/COLOR][/SIZE][/FONT]```

diff -uN UVCVIDEO_v0.1.0/uvc_video.c UVCVIDEO_patched/uvc_video.c
--- UVCVIDEO_v0.1.0/uvc_video.c    2008-06-26 10:41:01.000000000 +0200
+++ UVCVIDEO_patched/uvc_video.c    2008-06-26 14:03:58.000000000 +0200
@@ -371,23 +371,91 @@
     return data[0];
 }
 
+/* This patched function allows to overturn video images from an upside-down
+ * orientation to a normal one with mirrored effect. The conversion consists in
+ * reversing the order of the rows of imagines.
+ * "data" stores a sequence of pixels coming from the video source.
+ * This sequence is not a full frame or a full row of pixel, but just an
+ * ordered vector of pixels (from top-left to bottom-right), whose
+ * represents just an area of the current frame and which size ("nbytes") is
+ * not constant. In fact this function has to be called hundreds of times
+ * before a frame is completed. Each time "data" contains the next part of the
+ * current frame (upside-down). At the end data stored in "mem" buffer will be
+ * used by the application who requested the video stream.
+ * No memory allocation is needed because pixel order is modified directly
+ * while copying from "data" into "mem" buffer (i.e. in each call of this
+ * function), and not just once when the frame is already completed.
+ * This patch should work with all YUV image formats.
+ */
 static void uvc_video_decode_data(struct uvc_video_device *video,
         struct uvc_buffer *buf, const __u8 *data, int len)
 {
     struct uvc_video_queue *queue = &video->queue;
     unsigned int maxlen, nbytes;
     void *mem;
+    /* Patch variables */
+    unsigned int row_size, to_be_copied, shift_right;
 
     if (len <= 0)
         return;
 
     /* Copy the video data to the buffer. */
+    /* How many bytes are needed to complete the buffer? */
     maxlen = buf->buf.length - buf->buf.bytesused;
+    /* Where do pixels stored in "data" have to be copied? */
     mem = queue->mem + buf->buf.m.offset + buf->buf.bytesused;
+    /* How many bytes really can be copied into "mem"? */
     nbytes = min((unsigned int)len, maxlen);
-    memcpy(mem, data, nbytes);
-    buf->buf.bytesused += nbytes;
 
+    /* "row_size" is the number of bytes required to store a full row of
+     * the frame.
+     */
+    row_size = video->streaming->cur_frame->wWidth *
+           video->streaming->format->bpp / 8;
+    /* Each loop "nbytes" is decremented of the number of bytes just copied.
+     * So are there any other bytes to be copied?
+     */
+    while (nbytes > 0) {
+        /* As the rows of modified frames have to be fulfilled from
+         * bottom-left to top-right, each cycle tries to complete a
+         * single row.
+         * In this cycle where is it needed to start to store bytes
+         * within the selected row? From the beginning or shifted
+         * right? Because other bytes could have been already stored in
+         * that row without completing it, so it could be needed a right
+         * shift.
+         */
+        shift_right = buf->buf.bytesused % row_size;
+        /* In this cycle how many byte can we copy in the selected row?
+         */
+        if (nbytes > row_size - shift_right)
+            to_be_copied = row_size - shift_right ;
+        else
+            to_be_copied = nbytes;
+        /* "queue->mem + buf->buf.m.offset" is the base-address where to
+         * start to store the current frame. This address refers to a
+         * preallocated area (just for a sigle frame) taking part in a
+         * circular buffer, where to store a fixed number of sequent
+         * frames.
+         */
+        memcpy(queue->mem + buf->buf.m.offset
+               /* Go to the end of this frame. */
+               + row_size * video->streaming->cur_frame->wHeight
+               /* Go back for the number of bytes corrisponding to the
+                * already fully completed rows.
+            */
+               - (buf->buf.bytesused - shift_right)
+               /* Go back at the starting point of the upper row. */
+               - row_size
+               /* Shift right on this row if it is needed. */
+               + shift_right,
+               data,
+               to_be_copied );
+        /* Update "data", "byteused" and "nbytes" values. */
+        data += to_be_copied;
+        buf->buf.bytesused += to_be_copied ;
+        nbytes -= to_be_copied;
+    }
     /* Complete the current frame if the buffer size was exceeded. */
     if (len > maxlen) {
         uvc_trace(UVC_TRACE_FRAME, "Frame complete (overflow).\n");



```[FONT=Arial][SIZE=2][U][B][COLOR=Red]
SECOND SOLUTION ([SIZE=5]NOT[/SIZE] MIRRORED IMAGES)
[/COLOR][/B][/U][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Red]# modified June 26, 2008[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Red]
[/COLOR][/SIZE][/FONT]```

diff -uN UVCVIDEO_v0.1.0/uvc_video.c UVCVIDEO_patched/uvc_video.c
--- UVCVIDEO_v0.1.0/uvc_video.c    2008-06-26 10:41:01.000000000 +0200
+++ UVCVIDEO_patched/uvc_video.c    2008-06-26 14:03:58.000000000 +0200
@@ -371,23 +371,81 @@
     return data[0];
 }
 
+/* This patch should work ONLY with YUY2 image formats, also known as YUYV or
+ * YUV422 formats.
+ * This patched function allows to overturn video images from an upside-down
+ * orientation to a normal one. The conversion consists in copying 4 bytes at a
+ * time (Y0,U0,Y1,V0) corresponding to 2 pixels from the frame (coming from the
+ * video source) to the buffer that will be used by the application requesting
+ * the video stream. But in order to satisfy the YUY2 image format byte has to
+ * be copied in this way: Y1 U0 Y0 VO. Bytes are copied in a bottom-up
+ * direction into the reversed frame.
+ * "data" stores a sequence of pixels coming from the video source.
+ * This sequence is not a full frame or a full row of pixel, but just an
+ * ordered vector of pixels (from top-left to bottom-right), whose
+ * represents just an area of the current frame and which size ("nbytes") is
+ * not constant. In fact this function has to be called hundreds of times
+ * before a frame is completed. Each time "data" contains the next part of the
+ * current frame (upside-down). At the end data stored in "mem" buffer will be
+ * used by the application who requested the video stream.
+ * No memory allocation is needed because pixel order is modified directly
+ * while copying from "data" into "mem" buffer (i.e. in each call of this
+ * function), and not just once when the frame is already completed.
+ */
 static void uvc_video_decode_data(struct uvc_video_device *video,
         struct uvc_buffer *buf, const __u8 *data, int len)
 {
     struct uvc_video_queue *queue = &video->queue;
     unsigned int maxlen, nbytes;
     void *mem;
+    /* Patch variables */
+    unsigned int i, pixel_size;
+    __u8 *ptr_tmp;
 
     if (len <= 0)
         return;
 
     /* Copy the video data to the buffer. */
+    /* How many bytes are needed to complete the buffer? */
     maxlen = buf->buf.length - buf->buf.bytesused;
+    /* Where do pixels stored in "data" have to be copied? */
     mem = queue->mem + buf->buf.m.offset + buf->buf.bytesused;
+    /* How many bytes really can be copied into "mem"? */
     nbytes = min((unsigned int)len, maxlen);
-    memcpy(mem, data, nbytes);
-    buf->buf.bytesused += nbytes;
 
+    /* "pixel_size" depens on the pixel color depth (bpp),
+     * but in YUY2 image format is constant and equal to 2.
+     */
+    pixel_size = video->streaming->format->bpp / 8;
+    /* In each loop 4 bytes are modified and copied into "mem" buffer. */
+    for (i = 0; i < nbytes; i += 2 * pixel_size) {
+            /* "queue->mem + buf->buf.m.offset" is the base-address
+             * where to start to store the current frame. This
+             * address refers to a preallocated area (just for a
+             * sigle frame) taking part in a circular buffer, where
+             * to store a fixed number of sequent frames.
+             */    
+        ptr_tmp = (__u8 *)(queue->mem + buf->buf.m.offset
+            /* Go to the end of this frame. */
+            + video->streaming->cur_frame->wWidth * pixel_size
+            * video->streaming->cur_frame->wHeight
+            /* Go back for the number of already copied bytes. */
+            - buf->buf.bytesused
+            /* Go back for the number of bytes (4 bytes) to be
+             *  copied in this cycle.
+             */
+            - 2 * pixel_size);
+        /* The order of copied bytes is changed from
+         * (Y0 U0 Y1 V1) to (Y1 U0 Y0 V1), i.e. from
+         * (#0 #1 #2 #3) to (#2 #1 #0 #3).
+         */
+        ptr_tmp[0] = ((__u8 *)(data + i))[2];
+        ptr_tmp[1] = ((__u8 *)(data + i))[1];
+        ptr_tmp[2] = ((__u8 *)(data + i))[0];
+        ptr_tmp[3] = ((__u8 *)(data + i))[3];
+        /* Update "byteused" value. */
+        buf->buf.bytesused += 2 * pixel_size;
+    }
     /* Complete the current frame if the buffer size was exceeded. */
     if (len > maxlen) {
         uvc_trace(UVC_TRACE_FRAME, "Frame complete (overflow).\n");



```~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[SIZE=2]

Well, now the worst part has been done!!!
We just need to compile our modded file and to install the new driver, so from shell you have to go to the "Trunk" directory and type:
[/SIZE]```
make
```[SIZE=2]there shouldn't be errors!!

[/SIZE][SIZE=2]Then, ONLY if you are using one of the Ubuntu distributions (ubuntu, kubuntu, etc.), open with you editor the "Makefile" and change the following line:
[/SIZE]```
INSTALL_MOD_DIR := usb/media
```[SIZE=2]with
[/SIZE]```
INSTALL_MOD_DIR := ubuntu/media/usbvideo
```[SIZE=2]Now we just need to remove uvcvideo module (if you have previously installed it):
[/SIZE][SIZE=2]```
sudo modprobe -r uvcvideo
```Then:
```

sudo make install
sudo cp uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/
sudo cp uvcvideo.ko /lib/modules/`uname -r`/usb/media/
sudo depmod -ae
sudo modprobe -f uvcvideo

```Now everything should work!!!

Let me know!!

And please try both solutions..
in case you don't see any difference just use the **[COLOR=Red]SECOND[/COLOR]** solution (mirrored or not, has you prefer), it should be the safest!!

Good luck,
enjoy your webcam!! ;)

Arjos85 :guitar:

ps. excuse me for this too quick HOW-TO, without good explainations, but really just right now I haven't time to do it more verbose!!!
pps. excuse me also in case I made some mistakes!!!
[/SIZE]

---

### Post by Bazilio on 2008-06-23
wrong:
> **arjos85 said:**
> 
Then type:
```
sudo lsusb -d xxxx:yyyy -v | grep "14 video"
```

right:
```
sudo lsusb -d xxxx:yyyy -v | grep "14 Video"
```
"V" in "Video" in upper case

---

### Post by arjos85 on 2008-06-23
Really thank you Brazilio!!! ;)
I've just modified the HOW-TO!!!

ciao

---

### Post by Bazilio on 2008-06-25
> SECOND SOLUTION (NOT MIRRORED IMAGES)
# added June 24th, 2008
Perfect job!
Thank you, Marko!
Not mirrored image, not upside-down, with good quality!
I am very happi with it patch!

Thank you!

---

### Post by arjos85 on 2008-06-25
> **Bazilio said:**
> Perfect job!
Thank you, Marko!
Not mirrored image, not upside-down, with good quality!
I am very happi with it patch!

Thank you!


Thank you for having tried my patches..... :guitar:
it's a kind of test session....
for examplle someone has some problem with the second solution (not mirrored)!!

Which "not mirrored" solution have you tried?
The first or the second? ;)

---

### Post by Bazilio on 2008-06-25
i wrote in quote: SECOND SOLUTION (NOT MIRRORED IMAGES)

before i used SECOND SOLUTION (MIRRORED IMAGES)

---

### Post by arjos85 on 2008-06-25
Ah ok...
excuse me I'm still sleeping!! ;)

---

### Post by arjos85 on 2008-06-26
Hey guys,
I just want to inform you that I have modified the HOW-TO:
added patches and speed up the 2 versions of the first solution.

Let me know if you think there are any mistakes!!

Thanks a lot!!

Ciao Ciao

Arjos85

---

### Post by neandertal on 2008-06-27
Hi arjos85,
thank you for this how to. Every time I try to apply any of the four patches in the trunk folder I get an error message:  Hunk #1 FAILED at 371 1 out of 1 hunk FAILED -- saving rejects to file uvc_video.c.rej.

---

### Post by arjos85 on 2008-06-27
> **neandertal said:**
> Hi arjos85,
thank you for this how to. Every time I try to apply any of the four patches in the trunk folder I get an error message:  Hunk #1 FAILED at 371 1 out of 1 hunk FAILED -- saving rejects to file uvc_video.c.rej.

Please check if you have also copied the last blank line of the patch..it should be necessary to succeed the patching ;)

---

### Post by arjos85 on 2008-06-27
Excuse me I didn't mention it in the HOW-TO...
just for now ADD A BLANK LINE AT THE END OF EACH PATCH before applying it!!

:P

---

### Post by neandertal on 2008-06-27
I couldn't find any blank line so I tried to insert one but it didn't work.I am not very good with this patching stuff. I then decided to copy the line of code line by line to the uvc_vido.c (with removing all the + signs) and it worked!!!
 I still have to check stability and quality but the webcam image is no longer up side down. Thank you so much Arjos. Very good job.

---

### Post by arjos85 on 2008-06-27
> **neandertal said:**
> I couldn't find any blank line so I tried to insert one but it didn't work.
You are right...it's not possible to add a blank line at the end of a of a quote/code test.
> I am not very good with this patching stuff. I then decided to copy the line of code line by line to the uvc_vido.c (with removing all the + signs) and it worked!!!
 I still have to check stability and quality but the webcam image is no longer up side down. Thank you so much Arjos. Very good job.GREAT!!!
I m very happy my patch works also for you!!
Which patch have you tried?

However it should be a good thing if you try also the other 3 patches!!
Now you can simply donwload them in the Trunk folder because I've attached them at the end of the HOW-TO...
then with the shell go to inside the Trunk folder and do:
```
patch < the_patch_you_want 
```Please let me know about the performance of the all 4 patches!!
Thank you very much!! ;)

Ciao ciao
Arjos

---

### Post by napalm brain on 2008-06-28
So if you don't have a proprietary driver, this is worthless? I also have an inverted webcam but I've had absolutely not luck correcting the problem. I have an UVC webcam but yeah.

---

### Post by arjos85 on 2008-06-28
> **napalm brain said:**
> So if you don't have a proprietary driver, this is worthless? I also have an inverted webcam but I've had absolutely not luck correcting the problem. I have an UVC webcam but yeah.


Excuse me , I'm Italian and I'm not very good in English!! :S
What are you talking about when you said "this is worthless"?
I don't have a proprietary driver in the sense that it is not a SONIX driver (since my webcam is a SONIX one), but I'm using an open source driver: UVCVIDEO.
You said you also have an UVC webcam mounted upside-down...
have you tried one of my 4 solutions?
What do you need? Can I help you in some way?

Let me know...and please try to be more clear you can...
thank you.

Excuse me for my English!! ;)

arjos

---

### Post by arjos85 on 2008-06-29
> **Bazilio said:**
> Perfect job!
Thank you, Marko!
Not mirrored image, not upside-down, with good quality!
I am very happi with it patch!

Thank you!



Ehy Brazilio,
I've just find out you have talked about this how-to at bugs.launchpad.net ...
thank you very much...
it is very important for the linux/opensource community to disseminate information like that!!
also if it is not a real kernel/driver bug, you have helped all those people who think it is and go to bugs.launchpad.net!!

good job!! ;)

---

### Post by napalm brain on 2008-06-29
> **arjos85 said:**
> Excuse me , I'm Italian and I'm not very good in English!! :S
What are you talking about when you said "this is worthless"?
I don't have a proprietary driver in the sense that it is not a SONIX driver (since my webcam is a SONIX one), but I'm using an open source driver: UVCVIDEO.
You said you also have an UVC webcam mounted upside-down...
have you tried one of my 4 solutions?
What do you need? Can I help you in some way?

Let me know...and please try to be more clear you can...
thank you.

Excuse me for my English!! ;)

arjos

Ah, sorry. I was worried about that being misconstrued. I meant, I can't use your tutorial if I don't have a proprietary driver? It would be unfortunate but this would be the *way* to solve the issue. Although, yes I do have a UVC webcam also. Oddly enough, when I restart, **sometimes**, the webcam is fine. A bit unpredictable but if I can't use this, I will live.

:)

---

### Post by arjos85 on 2008-06-29
> **napalm brain said:**
> Ah, sorry. I was worried about that being misconstrued. I meant, I can't use your tutorial if I don't have a proprietary driver? It would be unfortunate but this would be the *way* to solve the issue. Although, yes I do have a UVC webcam also. Oddly enough, when I restart, **sometimes**, the webcam is fine. A bit unpredictable but if I can't use this, I will live.

:)

If I understood well...you have two webcams, the former is NOT uvc capable the latter is uvc capable.
Is it right?
Well...for the first one you have to look for some other solution...I don't know if the vendor released driver for you webcam, just try to look for it in the vendor website. Maybe someone of the opensource community has developed a driver for your webcam.

Please can you tell me the model of your webcams?

Thank you very much!!

ps.
where are you writing from?

---

### Post by leo_ietres on 2008-07-10
Ok, I corroborate that the first patch works perfectly on the PACKARD BELL BG45-P-025 laptop. 

here is the lsusb command on my laptop for users that could have the same one:

leonardo@leo-portatil:~$ lsusb
Bus 007 Device 002: ID 04f2:b012 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c03f Logitech, Inc. UltraX Optical Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by arjos85 on 2008-07-10
Hi leo_ietres,
> **leo_ietres said:**
> Ok, I corroborate that the first patch works perfectly on the PACKARD BELL BG45-P-025 laptop. 

leonardo@leo-portatil:~$ lsusb
Bus 007 Device 002: ID 04f2:b012 Chicony Electronics Co., Ltd 


Why don't you try also the second patch?
It should be more stable and faster!!

Thank you for having tried my patch!!
Enjoy your webcam!!

Ciao ciao

---

### Post by WillyLinux on 2008-07-15
> **leo_ietres said:**
> Ok, I corroborate that the first patch works perfectly on the PACKARD BELL BG45-P-025 laptop. 

here is the lsusb command on my laptop for users that could have the same one:

leonardo@leo-portatil:~$ lsusb
Bus 007 Device 002: ID 04f2:b012 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c03f Logitech, Inc. UltraX Optical Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
leo_ietres, can you tell me specifically how you did that?

I also have a Packard Bell Easynote BG45-P-025 and cannot solve the problem.

I'm running Ubuntu 8.04 64bits.
Image is seen in the right position in cheese (but too dark). Ekiga and Skype still show upside down. (I've tried all 4 solutions).

Thanks

---

### Post by arjos85 on 2008-07-15
> **WillyLinux said:**
> leo_ietres, can you tell me specifically how you did that?
I also have a Packard Bell Easynote BG45-P-025 and cannot solve the problem.
I'm running Ubuntu 8.04 64bits.

Hi WillyLinux,
are you getting any error while installing the patch/module?

It seems that the patch isn't applied and used...try to restart your system!!

Regards,
arjos85

---

### Post by WillyLinux on 2008-07-16
hi arjos85,
everythink seems to be working (at least I don't receive any warning or error).

Steps:
1.download files
2.change files makefile INSTALL_MOD_DIR	:= usb/media/usbvideo
3.download patch and copy to trunk folder
4.patch < filename

guillermo@rtpc:~/descargas/trunk$ patch < patch_solution1_mirrored.txt
patching file uvc_video.c
guillermo@rtpc:~/descargas/trunk$

(no error message. seems to be ok).

5.make

guillermo@rtpc:~/descargas/trunk$ make
Building USB Video Class driver...
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/guillermo/descargas/trunk/uvc_driver.o
  CC [M]  /home/guillermo/descargas/trunk/uvc_video.o
  LD [M]  /home/guillermo/descargas/trunk/uvcvideo.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/guillermo/descargas/trunk/uvcvideo.ko
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-19-generic'
guillermo@rtpc:~/descargas/trunk$

(seems to be no error)

6.7.8.

guillermo@rtpc:~/descargas/trunk$ sudo modprobe -r uvcvideo
[sudo] password for guillermo: 
guillermo@rtpc:~/descargas/trunk$ sudo make install
Installing USB Video Class driver...
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-19-generic'
  INSTALL /home/guillermo/descargas/trunk/uvcvideo.ko
  DEPMOD  2.6.24-19-generic
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-19-generic'
guillermo@rtpc:~/descargas/trunk$ sudo modprobe uvcvideo
guillermo@rtpc:~/descargas/trunk$ 


Something has been solved as in the camera software "cheese" the image has turned to normal position (but dark). In the other software there's no change at all.

Perhaps I'm forgetting something or applying something wrong?
rebooting the system doesn't change anything.

thanks!

---

### Post by arjos85 on 2008-07-16
> **WillyLinux said:**
> hi arjos85,
everythink seems to be working (at least I don't receive any warning or error).


well... I really don't know!!

Try this steps:
```
sudo find /lib/modules/ -name uvcvideo.ko  (give me the output)
sudo modprobe -r uvcvideo
sudo rm `find /lib/modules/2.6.24-19-generic/ -name uvcvideo.ko`
sudo make install
sudo cp uvcvideo.ko /lib/modules/2.6.24-19-generic/usb/media/
sudo depmod -ae
sudo modprobe -f uvcvideo
```Let me know,
thank  you!!

Regards,

arjos85

---

### Post by WillyLinux on 2008-07-16
It worked!

I've tried what you suggested and it worked (Ekiga works fine and Skype can transmit video properly -even tough I cannot see my own video in Skype, but this is a Skype matter I guess) another comment: cheese is not working after the changes, I removed it.

I don't know if the output you requested is useful now, but here it is:
/lib/modules/2.6.24-16-generic/ubuntu/media/usbvideo/uvcvideo.ko
/lib/modules/2.6.24-19-generic/usb/media/uvcvideo.ko
/lib/modules/2.6.24-19-generic/usb/media/usbvideo/uvcvideo.ko

Well, thanks a lot!
Regards

---

### Post by arjos85 on 2008-07-16
> **WillyLinux said:**
> It worked!

I've tried what you suggested and it worked [..]

Well, thanks a lot!
Regards

Thank you very much for having tried my patch..
thank yuo for having warned me about this problem...
i will update the HOW-TO!!

enjoy your webcam!! :D

Regards,
arjos85

---

### Post by jacortijo on 2008-07-20
congratulations man!!! it works perfectly... now no need to have windows vista any more just for the webcam... ;-)
only the speed is very slow but I guess this will be improved in the general driver! 

thanks a lot once more.

Jose

---

### Post by arjos85 on 2008-07-20
> **jacortijo said:**
> congratulations man!!! it works perfectly... now no need to have windows vista any more just for the webcam... ;-)
only the speed is very slow but I guess this will be improved in the general driver! 

thanks a lot once more.

Jose

Ciao jacortijo,
very happy my patches works also with you!!

What webcam do you have ?
Which of the 4 patches have you applied?

let me know!! ;)
Regards

---

### Post by Ripichip on 2008-07-26
Great work!! =D 2 image mirror patch work for me!! !THANKS!!! =D
Packard Bell Easynote BG45-U-033 Ubuntu Hardy x64
Bus 007 Device 002: ID 04f2:b012 Chicony Electronics Co., Ltd

---

### Post by arjos85 on 2008-07-26
> **Ripichip said:**
> Great work!! =D 2 image mirror patch work for me!! !THANKS!!! =D
Packard Bell Easynote BG45-U-033 Ubuntu Hardy x64
Bus 007 Device 002: ID 04f2:b012 Chicony Electronics Co., Ltd


Thank you for informing me about your configuration...
have you tried the other patches? ;)

---

### Post by Ripichip on 2008-07-26
I probe de first and second patch image mirror, but de second patch work fine that the other, because the second i have one image more fluid... (Sorry mi bad english xD)
My test i did in the program Cheese.

---

### Post by arjos85 on 2008-07-26
> **Ripichip said:**
> I probe de first and second patch image mirror, but de second patch work fine that the other, because the second i have one image more fluid... (Sorry mi bad english xD)
My test i did in the program Cheese.

ah ah :D
don t worry for your English!!! :P
 where are you from?

However thank you for reporting me your test details!! 

ciao ciao
arjos85
;)

---

### Post by Bazilio on 2008-07-30
I updated my system and image becam upside-down again, and colors becam bad.
I desided to update uvc driver from svn.
Then I aplied pach (2 not mirrored) image not upside-down, but colors steel bad.
Any ideas?

---

### Post by arjos85 on 2008-07-30
> **Bazilio said:**
> I updated my system and image becam upside-down again, and colors becam bad.
I desided to update uvc driver from svn.
Then I aplied pach (2 not mirrored) image not upside-down, but colors steel bad.
Any ideas?

Well I don't know...
try also the other 3 patches...and report me what you get!!

;)

---

### Post by Bazilio on 2008-07-31
This is translate for russian users: [http://forum.ubuntu.ru/index.php?topic=23660.msg233306#msg233306](http://forum.ubuntu.ru/index.php?topic=23660.msg233306#msg233306)

---

### Post by arjos85 on 2008-07-31
> **Bazilio said:**
> This is translate for russian users: [http://forum.ubuntu.ru/index.php?topic=23660.msg233306#msg233306](http://forum.ubuntu.ru/index.php?topic=23660.msg233306#msg233306)


Thank you Brazilio for making my patches more popular!! ;)
Have you solved the problems you got after last installation??

CIao Ciao
Marco

---

### Post by Bazilio on 2008-07-31
> **arjos85 said:**
> Thank you Brazilio for making my patches more popular!! ;)
Have you solved the problems you got after last installation??

CIao Ciao
Marco
no, the problem still exists. no red color.
but it can be solved by tune some settings. in kopete it works, in skype i don't have any settings...

P.S. People solving the problem, Your patch works, thank you!

---

### Post by arjos85 on 2008-08-02
> **Bazilio said:**
> no, the problem still exists. no red color.
but it can be solved by tune some settings. in kopete it works, in skype i don't have any settings...

P.S. People solving the problem, Your patch works, thank you!

Just right now I've compared my patch with the last version of uvcvideo driver. The file I've modified (uvc_video.c) is now changed, but the function I've modded is unchanded.
So please try to apply the patch manually and not with "patch" command.

I hope this could help...

ciao

Marco

---

### Post by Bazilio on 2008-08-04
it was false alarm :)
in skype, cheese and kopete image looks good now.. but I did nothing.. just updated nvidia drivers... magic...

Update:
Oh, I know, what it was! I ajusted colors in kopete settings and it aplied to all applications - in skype, cheese, both kopete (kde3, kde4).
If I change settings in kopete it change some global settings.
(I hope you understand me, sorry for my english)

---

### Post by arjos85 on 2008-08-04
> **Bazilio said:**
> it was false alarm :)
in skype, cheese and kopete image looks good now.. but I did nothing.. just updated nvidia drivers... magic...

Update:
Oh, I know, what it was! I ajusted colors in kopete settings and it aplied to all applications - in skype, cheese, both kopete (kde3, kde4).
If I change settings in kopete it change some global settings.
(I hope you understand me, sorry for my english)

WOW..
I did't know about this issue, thank you for reporting me.
However don't worry, your English is good...also my English is not perfect!!

Ciao
marco

---

### Post by amsterbran on 2008-08-04
hi! thanks for all your work...

however, my system hangs when installing the patches. specifically, i believe it hangs on the main for loop you have added.

i'm running ubuntu 8.04 on a lenovo ideapad y510. there is an integrated "lenovo easy camera", and the image is upside down in every application i've tried. it is a uvc based webcam. someone else with my computer apparently had the same problem..see the link below, post #24.

[http://ubuntuforums.org/showthread.php?t=870681&page=3](http://ubuntuforums.org/showthread.php?t=870681&page=3)


any ideas or help would be appreciated!! thanks again!!

---

### Post by arjos85 on 2008-08-04
> **amsterbran said:**
> hi! thanks for all your work...

however, my system hangs when installing the patches. specifically, i believe it hangs on the main for loop you have added.

i'm running ubuntu 8.04 on a lenovo ideapad y510. there is an integrated "lenovo easy camera", and the image is upside down in every application i've tried. it is a uvc based webcam. someone else with my computer apparently had the same problem..see the link below, post #24.

[http://ubuntuforums.org/showthread.php?t=870681&page=3](http://ubuntuforums.org/showthread.php?t=870681&page=3)


any ideas or help would be appreciated!! thanks again!!

Well...
have you tried all the 4 patches?
Let try and let me know!!

Regards,
Marco

---

### Post by pbouf on 2008-08-09
I've tried all 4 and get a system freeze when I start Cheese each time.

How can I get back to whatever I had before--upside down webcam was better than a frozen system. :)

---

### Post by arjos85 on 2008-08-09
> **pbouf said:**
> I've tried all 4 and get a system freeze when I start Cheese each time.

How can I get back to whatever I had before--upside down webcam was better than a frozen system. :)

I'm really sorry that you have this kind of problem.
have you tried to patch your uvcvideo.c by hand?
It could be possible that you have downloaded the last version of the uvc driver and maybe the uvcvideo.c file has been modified, so that my patch can't be applied correctly.
However if I remember well, Cheese doesn't work at all with uvcvideo driver.
Have you tried other programs, i.e. "luvcview", "skype", msn?
To take your system back, just download the last version of uvc driver and install it.

Regards,

Marco

---

### Post by benidelaserena on 2008-08-09
Work both solutions.
Hardy Heron.
Asus GS2
Camera in... Bus 006 Device 002: ID 174f:5a35

---

### Post by pbouf on 2008-08-09
Skype also freezes after the patch--both Skype and Cheese seemed to work okay except upside-down before. I haven't tried the other two you mention. I downloaded the latest available (SVN r242) uvc driver; what rev did you use? I think I'd rather just patch the exact same sources as you did rather than try to patch manually.

Thanks for your help, hopefully almost there.. In a couple of days, I have to pass this laptop along to folks who definitely wont be applying patchfiles and such, and I won't be able to access it remotely either.
Cheers.

---

### Post by arjos85 on 2008-08-09
> **pbouf said:**
> Skype also freezes after the patch--both Skype and Cheese seemed to work okay except upside-down before. I haven't tried the other two you mention. I downloaded the latest available (SVN r242) uvc driver; what rev did you use? I think I'd rather just patch the exact same sources as you did rather than try to patch manually.

Thanks for your help, hopefully almost there.. In a couple of days, I have to pass this laptop along to folks who definitely wont be applying patchfiles and such, and I won't be able to access it remotely either.
Cheers.

OK..
but please try just this 4 steps:
1) download a fresh new copy of the driver;
2) open "uvcvideo.c" file and substitute the whole "uvc_video_decode_data()" function with these lines:
```

static void uvc_video_decode_data(struct uvc_video_device *video,
        struct uvc_buffer *buf, const __u8 *data, int len)
{
    struct uvc_video_queue *queue = &video->queue;
    unsigned int maxlen, nbytes;
    void *mem;

    unsigned int i, pixel_size;
    __u8 *ptr_tmp;

    if (len <= 0)
        return;

    maxlen = buf->buf.length - buf->buf.bytesused;
    mem = queue->mem + buf->buf.m.offset + buf->buf.bytesused;
    nbytes = min((unsigned int)len, maxlen);

    pixel_size = video->streaming->format->bpp / 8;
    for (i = 0; i < nbytes; i += 2 * pixel_size) {
        ptr_tmp = (__u8 *)(queue->mem + buf->buf.m.offset

            + video->streaming->cur_frame->wWidth * pixel_size
            * video->streaming->cur_frame->wHeight
            - buf->buf.bytesused
            - 2 * pixel_size);
        ptr_tmp[0] = ((__u8 *)(data + i))[2];
        ptr_tmp[1] = ((__u8 *)(data + i))[1];
        ptr_tmp[2] = ((__u8 *)(data + i))[0];
        ptr_tmp[3] = ((__u8 *)(data + i))[3];
        buf->buf.bytesused += 2 * pixel_size;
    }
    if (len > maxlen) {
        uvc_trace(UVC_TRACE_FRAME, "Frame complete (overflow).\n");
        buf->state = UVC_BUF_STATE_DONE;
    }
}

```
3) Install again the driver with the following commands from the shell:
   - move into the folder in which you saved the new copy of the driver (and where there is the uvcvideo.c file you modified just in the step before)
```
   $ sudo modprobe -r uvcvideo
   $ make
   $ sudo make install
   $ sudo cp uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/
   $ sudo cp uvcvideo.ko /lib/modules/`uname -r`/usb/media/
   $ sudo depmod -ae
   $ sudo modprobe -f uvcvideo

```
4) Install LUVCVIEW from your packages manager and try these commands:
```
   $ luvcview 
   $ luvcview -f yuv

```   Report me what you get!!

I hope these few steps can solve your problem!!
Let me know!!

Regards

Marco

---

### Post by pbouf on 2008-08-10
Thanks, I just tried that but I still get a freeze (for both of the luvcview commands).

---

### Post by arjos85 on 2008-08-10
> **pbouf said:**
> Thanks, I just tried that but I still get a freeze (for both of the luvcview commands).

OK,
at the moment I really don't know how to solve this problem, also because I don't know anything about your system.
Which camera do you have?
Can you post me the results of these commands?
$ lsusb
$ sudo lsusb -vv
$ dmesg | grep uvc

Thank you
Regards
Marco

---

### Post by pbouf on 2008-08-10
lsusb:

```
Bus 007 Device 002: ID 5986:0200 Bison 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

sudo lsusb -vv: see attachment

dmesg | grep uvc:
```
[   28.913146] uvcvideo: Found UVC 1.00 device Lenovo Easy Camera (5986:0200)
[   29.870596] usbcore: registered new interface driver uvcvideo
```

Also, uname -r:
2.6.24-19-generic

---

### Post by arjos85 on 2008-08-10
> **pbouf said:**
> lsusb:

```
Bus 007 Device 002: ID 5986:0200 Bison 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```sudo lsusb -vv: see attachment

dmesg | grep uvc:
```
[   28.913146] uvcvideo: Found UVC 1.00 device Lenovo Easy Camera (5986:0200)
[   29.870596] usbcore: registered new interface driver uvcvideo
```Also, uname -r:
2.6.24-19-generic

Ah ok...
maybe I've understood why my patch doesn't work with your webcam...
If I've understood well, your webcam doesn't use YUV format as image format...
but my patch works just with YUV images as I wrote in the HOW-TO.

Just post the result of this command:
$ luvcview -L

Regards,
Marco

---

### Post by pbouf on 2008-08-10
```
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
/dev/video0 does not support read i/o
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 1280, height = 1024 }
    Time interval between frame: 1/15, 1/7, 
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 1280, height = 1024 }
    Time interval between frame: 1/7,
```

---

### Post by arjos85 on 2008-08-10
> **pbouf said:**
> ```
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
/dev/video0 does not support read i/o
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 1280, height = 1024 }
    Time interval between frame: 1/15, 1/7, 
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 1/10, 
{ discrete: width = 1280, height = 1024 }
    Time interval between frame: 1/7,
```


Really really strange!!
Your webcam should work!!
Maybe the uvcvideo driver has been modified in such a way my patch can't work anymore.
But I don't think this is true...!!!
As attachement you can find the already patched driver I use myself on my laptop...try to install it!!
I hope this could help...

regards,
Marco

---

### Post by pbouf on 2008-08-10
Ok, so that at least gets a working luvcview, though if I try to maximize/restore the window it sometimes segfaults. And it's still upside down. :)

Edit: Also, Cheese works, but still upside-down.

---

### Post by arjos85 on 2008-08-10
> **pbouf said:**
> Ok, so that at least gets a working luvcview, though if I try to maximize/restore the window it sometimes segfaults. And it's still upside down. :)

Unbelievable!!!
Well...just try to ask for help in the uvcvideo mailing list: [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

I hope there someone else can help you!!
I'm so sorry my patch doesn't work with you!!  :(

Regards,
Marco

---

### Post by pbouf on 2008-08-10
Thanks anyway for all your help. One question -- is there a way to be 100% sure that my system is actually using the uvc driver that I've compiled from your patched sources? If I understand your last post, the image should be right-side-up, if it works at all.

---

### Post by arjos85 on 2008-08-10
> **pbouf said:**
> Thanks anyway for all your help. One question -- is there a way to be 100% sure that my system is actually using the uvc driver that I've compiled from your patched sources? If I understand your last post, the image should be right-side-up, if it works at all.

Try this command:
    $ lsmod | grep uvcvideo
on my system I get this output, you should get something similar:
uvcvideo               60040  0
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
usbcore               146028  5 uvcvideo,hci_usb,ehci_hcd,uhci_hcd

Then try also :
$ sudo modprobe -r uvcvideo
$ sudo depmod -ae
$ sudo modprobe -f uvcvideo
$ dmesg | tail

Let me know,
marco

---

### Post by pbouf on 2008-08-10
```
[   31.790324] usbcore: deregistering interface driver uvcvideo
[   33.554191] v4l2_common: no version for "struct_module" found: kernel tainted.
[   33.554209] v4l2_common: no version magic, tainting kernel.
[   33.560503] v4l1_compat: no version magic, tainting kernel.
[   33.565453] videodev: no version magic, tainting kernel.
[   33.567502] Linux video capture interface: v2.00
[   33.568461] compat_ioctl32: no version magic, tainting kernel.
[   33.572896] uvcvideo: no version magic, tainting kernel.
[   33.577804] uvcvideo: Found UVC 1.00 device Lenovo Easy Camera (5986:0200)
[   33.745089] input: Lenovo Easy Camera as /devices/pci0000:00/0000:00:1d.7/usb7/7-6/7-6:1.0/input/input10
[   33.912692] uvcvideo: Failed to query (1) UVC control 2 (unit 4) : -32 (exp. 8).
[   33.912702] uvcvideo: I2C dev 0x60 register 0x0a = 0x00 | i2c_req : [0x60][0x01][0x0a][0x00][0x00][0x00][0x00][0xff] 
[   34.072878] uvcvideo: Failed to query (129) UVC control 2 (unit 4) : -32 (exp. 8).
[   34.072890] uvcvideo: I2C dev 0x00 register 0x00 = 0x00 | i2c_req : [0x00][0x00][0x00][0x00][0x00][0x00][0x00][0x00] 
[   34.073868] uvcvideo: Failed to query (1) UVC control 2 (unit 4) : -32 (exp. 8).
[   34.073876] uvcvideo: I2C dev 0x60 register 0x0b = 0x00 | i2c_req : [0x60][0x01][0x0b][0x00][0x00][0x00][0x00][0xff] 
[   34.074370] uvcvideo: Failed to query (129) UVC control 2 (unit 4) : -32 (exp. 8).
[   34.074377] uvcvideo: I2C dev 0x00 register 0x00 = 0x00 | i2c_req : [0x00][0x00][0x00][0x00][0x00][0x00][0x00][0x00] 
[   34.074416] usbcore: registered new interface driver uvcvideo
[   34.074422] USB Video Class driver (v0.1.0)
```

---

### Post by arjos85 on 2008-08-11
mhhhhh...
something seems to be wrong on your system:
[   33.554191] v4l2_common: no version for "struct_module" found: kernel tainted.
 [   33.554209] v4l2_common: no version magic, tainting kernel.
 [   33.560503] v4l1_compat: no version magic, tainting kernel.
 [   33.565453] videodev: no version magic, tainting kernel.
 [   33.568461] compat_ioctl32: no version magic, tainting kernel.
 [   33.572896] uvcvideo: no version magic, tainting kernel.

The lines above are very strange. It seems your v4l2 doesn't have any definition for "struct_module"....
maybe your v4l2 is too old!!

Try to install the newest version of v4l2 module.
And look through internet for any solution to your problem...

Good luck!!

Marco

---

### Post by amsterbran on 2008-08-14
same problem, same webcam (and i'm assuming same machine, ideapad y510?) as pbouf.

any luck lately, pbouf? i've tried so many things.

---

### Post by pbouf on 2008-08-15
amsterbran: sorry, no. And the Y510 is out of my hands now. Hopefully a straightforward fix will surface sometime soon. I can't expect the proud new owners of this laptop to do much more than 'sudo apt-get install rightside-up-webcam'... ;)

---

### Post by w_daniel on 2008-08-24
Hi everyone. I've got laptop Asus F3Series and I have the same problem: the patches didn't work. The output of my lsusb command:

Bus 007 Device 003: ID 04ca:f016 Lite-On Technology Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 174f:5a35 Syntek 1.3MPixel Web Cam - Asus G1s
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I made everything as in how-to but without success, my webcam's output is still upside-down :confused:

Thanks

---

### Post by jacobleonardking on 2008-08-25
I'm having the same problems as pbrouf and amsterbran (same laptop: Y510).

Have any y510 owners had any luck with this patch?

Thanks,
Jacob

---

### Post by amsterbran on 2008-08-28
> **jacobleonardking said:**
> I'm having the same problems as pbrouf and amsterbran (same laptop: Y510).

Have any y510 owners had any luck with this patch?

Thanks,
Jacob

No luck..I have a y510 as well. I was trying a few things to fix it..mainly things like this

[http://forum.skype.com/index.php?showtopic=112470&st=0&p=511530&#entry511530](http://forum.skype.com/index.php?showtopic=112470&st=0&p=511530&#entry511530)

and

[http://ubuntuforums.org/showthread.php?t=725179](http://ubuntuforums.org/showthread.php?t=725179)

but i haven't had much time lately..

---

### Post by jacobleonardking on 2008-09-07
So, I finally gave up on inverting the camera in software, ripped the top half of my laptop apart and physically inverted the camera.

Now, it works fine if I boot off the Ubuntu LiveCD and run any software that uses the webcam.

However, in the process of trying the patch in this thread, if I boot off my hard disk, anything that tries to access the camera makes the machine hang, with the caps lock and scroll lock lights blinking. Can't even Ctrl-Alt-F1. Any idea how to revert to the old driver? Of course, I could just reinstall Ubuntu, but there must be an easier solution.

Simply installing the trunk without the patch doesn't change anything.

Thanks,
Jacob

---

### Post by Cyprus on 2008-09-10
Hi,

I tested first the 2nd solution and "lost" the cam (not in lsusb result anymore); no way back by making with the other solutions, even without patching.
My config: ubuntu 8.04 on Lenovo Ideapad Y510. 
"lsmod | grep uvcvideo" gives:
uvcvideo               59656  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
usbcore               146028  5 uvcvideo,usbhid,uhci_hcd,ehci_hcd

with dmesg, some new errors (linked ?):
[  123.450587] usb 7-2: new full speed USB device using uhci_hcd and address 18
[  123.457805] usb 7-2: device descriptor read/64, error -71
[  123.487064] usb 7-2: device descriptor read/64, error -71
[  123.499925] usb 7-2: new full speed USB device using uhci_hcd and address 19
[  123.505047] usb 7-2: device descriptor read/64, error -71
[  123.510933] usb 7-2: device descriptor read/64, error -71
[  123.520855] usb 7-2: new full speed USB device using uhci_hcd and address 20
[  123.541759] usb 7-2: device not accepting address 20, error -71
[  123.551225] usb 7-2: new full speed USB device using uhci_hcd and address 21
[  123.561921] usb 7-2: device not accepting address 21, error -71

Thanks for your help

---

### Post by Cyprus on 2008-09-11
Ok, uvcvideo is reinstalled. The 2 solutions tested; no correction. No problem anymore except the upside down image. Sorry.

No way to go back with the procedure described in this discussion: Y510 out of my hands, even without patch.
Instead (maybe source problem):
[B]svn checkout [http://svn.berlios.de/svnroot/repos/linux-uvc/](http://svn.berlios.de/svnroot/repos/linux-uvc/)
cd linux-uvc/linux-uvc/trunk
make
sudo make install[/B]
reboot (robust newbie's trick, actually after reinstalling)

(Patches tested with svn.berlios.de/svnroot/repos/linux-uvc/ )

I updated libpt-1.10.10-plugins-v4l2 with libpt-1.11.2-plugins-v4l2

"**luvcview**" hangs
"**luvcview -f yuv**" works fine (upside down)

---

### Post by Chybeck on 2008-09-21
Hi, 

I have an Asus X53SA , webcam 174f:5a35 , I used patch 1 it work ! .
With patch 2 , webcam seams laggy .

I'll run more tests , thanks u very much !
[http://doc.ubuntu-fr.org/x53sa](http://doc.ubuntu-fr.org/x53sa)

---

### Post by mexus on 2008-09-25
all 4 doesn't work image is still flipped.
On ASUS f3ke laptop running kubuntu 8.04, chicony 1.3mpx webcam

---

### Post by Anonym5555 on 2008-10-01
It works for me:

fujitsu U1010
webcam info: Bus 005 Device 004: ID 05ca:1841 Ricoh Co., Ltd 
driver: r5u870

I tried both options 'solution2', and both worked at the very first attempt, with cheese and skype!!

Many thanks for your work!!

---

### Post by AlexH76 on 2008-10-06
Great,
I'm on Asus x71a, solution2 (w/o mirrored image) works fine for me!
thx

---

### Post by Espadon on 2008-10-11
Fine,
I'm on Asus x53sa, solution1 w mirrored image works for me!

Thanks

---

### Post by caglar.dursun on 2008-10-23
When i try to make install i get 2 errors.
make empty variable name stoped.
make install Error 2

Do you have any suggestion ?

---

### Post by caglar.dursun on 2008-10-24
I downloaded your patch file in tar archive.Still nothing...There is no result.The strange things, I have same device that u said.But there is no solution.

This is the result of lsusb :

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 174f:5a35  -> Same cam model u said
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

And this is the result of luvcview -L

luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
/dev/video0 does not support read i/o
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 1/1, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 1/1, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 1/1, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 1/1, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 1/1, 
{ discrete: width = 1280, height = 960 }
	Time interval between frame: 1/9, 1/5, 1/1, 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 1/9, 1/5, 1/1, 

I dont get it.What the hell is wrong this things.

---

### Post by caglar.dursun on 2008-10-27
Hi, there is still no working answer about this issue.I try to reinstall driver module.I almost checked every article about this web cam problem but some of svn repository doesn't exist anymore or the procedure not work for my laptop cam.

I did every procedure like written in this article but when i write luvcview -L  I saw the one line which is written /dev/video0 does not support read i/o.Is that means I cannot use the cam anymore ?


What i have to do right now? I'm gonna lose my mind.

---

### Post by quini on 2008-10-31
Hi!

I've got a Sony Vaio TZ11MN; it's got a Ricoh usb camera, also supported through the r5u870 driver, but it doesn't seem to compile under the 2.6.27 kernel:

[http://ubuntuforums.org/showthread.php?t=927454&highlight=r5u870]("http://ubuntuforums.org/showthread.php?t=927454&highlight=r5u870")

Here's the exact camera model:

```
quini@quinitz:~$ lsusb | grep -i ricoh
Bus 005 Device 005: ID 05ca:183a Ricoh Co., Ltd
```

I had the hope uvcvideo could also support it, as it seems to fit the needs:

```
quini@quinitz:~$ sudo lsusb -d 05ca:183a -v | grep "14 Video"
[sudo] password for quini: 
      bFunctionClass         14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
```

But I've had no luck; all 4 solutions get the same dmesg output:

```
[ 4604.894885] Linux video capture interface: v2.00
[ 4604.923883] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183a)
[ 4604.926075] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[ 4604.926326] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[ 4604.926335] uvcvideo: Failed to initialize the device (-5).
[ 4604.926637] usbcore: registered new interface driver uvcvideo
[ 4604.926647] USB Video Class driver (SVN r262)
```

Help would be appreciated.  TIA  :KS

---

### Post by natpu0t on 2008-11-06
Hi!
First of all I want to say thank you for the great work!
But I have a problem. I have an asus u6s with this webcam:
```
Bus 007 Device 004: ID 090c:e370 Feiya Technology Corp.

```

The patch "patch_solution2_mirrored" worked fine for me on ubuntu 8.04 hardy, but under ubuntu 8.10 intrepid final, no one of the patches working. the picture is still upside down. Do you have any idea how I could fix that?
Or maybe somebody else? I will be very appreciate!
PS: Sorry for my English! I'm a russian.

---

### Post by pall.e on 2008-11-07
Natppu0t, I had the same problem and also have a Asus U6. After playing around with it for the last 3 hours, trying to reapply every patch nothing worked.  I did finally get it to work though.  I think what I did was apply the patch manually instead of using the patch command, but as I am a linux noob I am not quite sure what I did so instead I will explain exactly what I did.  
This is what I did:
```
 svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk 
```
(this gets the newest driver) then 
1) open "uvcvideo.c" in the trunk folder and substitute the whole "uvc_video_decode_data()" function with these lines:
```
{
    struct uvc_video_queue *queue = &video->queue;
    unsigned int maxlen, nbytes;
    void *mem;

    unsigned int i, pixel_size;
    __u8 *ptr_tmp;

    if (len <= 0)
        return;

    maxlen = buf->buf.length - buf->buf.bytesused;
    mem = queue->mem + buf->buf.m.offset + buf->buf.bytesused;
    nbytes = min((unsigned int)len, maxlen);

    pixel_size = video->streaming->format->bpp / 8;
    for (i = 0; i < nbytes; i += 2 * pixel_size) {
        ptr_tmp = (__u8 *)(queue->mem + buf->buf.m.offset

            + video->streaming->cur_frame->wWidth * pixel_size
            * video->streaming->cur_frame->wHeight
            - buf->buf.bytesused
            - 2 * pixel_size);
        ptr_tmp[0] = ((__u8 *)(data + i))[2];
        ptr_tmp[1] = ((__u8 *)(data + i))[1];
        ptr_tmp[2] = ((__u8 *)(data + i))[0];
        ptr_tmp[3] = ((__u8 *)(data + i))[3];
        buf->buf.bytesused += 2 * pixel_size;
    }
    if (len > maxlen) {
        uvc_trace(UVC_TRACE_FRAME, "Frame complete (overflow).\n");
        buf->state = UVC_BUF_STATE_DONE;
    }
}


```
Then run this code in the terminal 
```
 $ sudo modprobe -r uvcvideo
   $ make
   $ sudo make install
   $ sudo cp uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/
   $ sudo cp uvcvideo.ko /lib/modules/`uname -r`/usb/media/
   $ sudo depmod -ae
   $ sudo modprobe uvcvideo
```

That fixed it for me.  I stole most of my solution from arjos85 post 47 in this thread.  Let me know if it works.  Also pm and tell me if you have your suspend working on your u6.

---

### Post by FredFlintston on 2008-11-13
Thanks for the patch.  It seems to have fixed the problem for me on my ASUS G1S.  Oh...I did use the deprecated version from SVN rather than the one from linuxtv.org (the one the deprecated version tells you about when you attempt to build it).  Thanks again for the fairly painless solution.

---

### Post by bitokarox on 2008-11-16
Hi everyone!!

I'm new on this Linux world, so I'm sorry for my ignorance :(

I have an ASUS F3SA laptop, with the webcam installed on:

**Bus 006 Device 002: ID 174f:5a35  **

I did all the commands as says the HOW-TO, but I just can't apply the patch!

I'm in the trunk folder, downloaded the second solution (not mirrored image), renamed it for uvc_video_solution2.patch in the trunk folder, but when I issue the command 
**patch < uvc_video_solution1.patch** 
it says that the program patch isn't installed...

I've tried to search the file uvc_video.c but doesn't gives me any results. :'(

Does anyone know what I'm doing wrong?
Thanks everyone ! :D

---

### Post by tsl on 2008-11-19
Hi All,


I have an Asus U6S running Intrepid Ibex (kernel 2.6.27-7-generic).

From lsusb my webcam is a 04f2:b036 Chicony Electronics Co., Ltd 

Here is how I got my webcam working properly:

- sudo apt-get install subversion
- svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
patched the file with not mirrored patch #2
- make uvcvideo
- modified Makefile with the INSTALL_MOD_DIR := ubuntu/media/usbvideo
- sudo modprobe -r uvcvideo
- sudo make install
- sudo depmod -ae
- sudo modprobe uvcvideo

Everything working well!

Thanks!

---

### Post by yannux on 2008-11-30
Applied patch2 mirrored  and works perfectly :)

Thanks !!

---

### Post by damuffinman on 2008-12-01
Hi all, I've got this working before using Ubuntu 8.04 but I'm giving Fedora 10 a try this time round...

right now I'm stuck on the step when you do "make uvcvideo". I get the following error once I type "make uvcvideo" in root:

Building USB Video Class driver...
make: *** /lib/modules/2.6.27.5-117.fc10.x86_64/build: No such file or directory.  Stop.

Any light on this?

---

### Post by nightfrost on 2008-12-08
Any chance any of these patches will end up in trunk?

---

### Post by arjos85 on 2008-12-14
Ehj nighfrost, unluckly the creator of UVC driver told me that my patch won't be included in the trunk because the driver must work in kernel space, but every modification to the images coming from the camera has to be done in user space!!  ;(

---

### Post by arjos85 on 2008-12-14
However I've changed the HOW-TO in order to improve the installation procedure after the application of the patch!!
Unluckily with the new versions of UVC driver it can be impossible to apply my patches...in this case you should apply it my hand!! :S

---

### Post by degraaf on 2008-12-14
arjos85:
Thank you for creating this solution to the upside-down image problem.
Your solution works perfectly on my new Asus N10JA2 netbook and solves
the last problem I've been struggling to fix.  The camera shows up as
  Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 
and I'm running Fedora 10 with kernel-2.6.27.7-134.fc10.i686.

Your patches compile without error and run perfectly.  Since the image
was rotated 180 deg, not flipped, the NOTmirrored patches provide the
proper correction.  Both patch_solution1_NOTmirrored.txt and
patch_solution2_NOTmirrored.txt work indistinguishably, so I will
stick with the latter, as you recommend.

I surely hope that these patches will soon be added to the "official"
uvcvideo.ko module, as load options.

---

### Post by nightfrost on 2008-12-14
> **arjos85 said:**
> Ehj nighfrost, unluckly the creator of UVC driver told me that my patch won't be included in the trunk because the driver must work in kernel space, but every modification to the images coming from the camera has to be done in user space!!  ;(

Too bad, really.
But the syntek driver, it does basically the same thing your patch does for uvcvideo. How do you think that driver does it? In kernel space?

---

### Post by SubluminalAd on 2008-12-20
Using the solution referred to before, everything is okay until 

$ sudo cp uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/

but when I type 

   $ sudo cp uvcvideo.ko /lib/modules/`uname -r`/usb/media/

I get this output;

cp: cannot create regular file `/lib/modules/2.6.27-9-generic/usb/media/': No such file or directory

Any help would be appreciated - thanks in advance!

---

### Post by nightfrost on 2008-12-20
> **SubluminalAd said:**
> Using the solution referred to before, everything is okay until 

$ sudo cp uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/

but when I type 

   $ sudo cp uvcvideo.ko /lib/modules/`uname -r`/usb/media/

I get this output;

cp: cannot create regular file `/lib/modules/2.6.27-9-generic/usb/media/': No such file or directory

Any help would be appreciated - thanks in advance!

You're getting that error because there's no `/lib/modules/2.6.27-9-generic/usb/media/' dir. What you should do, is to place yourself in the modules root directory (i.e. "cd /lib/modules/`uname -r`"). There, you can issue "find -name 'uvcvideo.ko'", to see which directory the module lives in to start with. Finally you make a backup of the old uvcvideo.ko module and copy your new one there.

---

### Post by degraaf on 2008-12-27
A new kernel for Fedora 10 - kernel-2.6.27.9-159.fc10.i686 seems to have broken some code.  A make fails like this:

Building USB Video Class driver...
make[1]: Entering directory `/usr/src/kernels/2.6.27.9-159.fc10.i686'
  CC [M]  /home/usr.local/src/uvcvideo/trunk2/trunk/uvc_driver.o
In file included from /home/usr.local/src/uvcvideo/trunk2/trunk/uvcvideo.h:8,
                 from /home/usr.local/src/uvcvideo/trunk2/trunk/uvc_driver.c:41:
/home/usr.local/src/uvcvideo/trunk2/trunk/uvc_compat.h:346: error: redefinition 
of ‘video_drvdata’
include/media/v4l2-dev.h:121: error: previous definition of ‘video_drvdata’ was 
here
make[2]: *** [/home/usr.local/src/uvcvideo/trunk2/trunk/uvc_driver.o] Error 1
make[1]: *** [_module_/home/usr.local/src/uvcvideo/trunk2/trunk] Error 2
make[1]: Leaving directory `/usr/src/kernels/2.6.27.9-159.fc10.i686'
make: *** [uvcvideo] Error 2


I discovered a simple fix that allows make to work again:

$ diff uvc_compat.hSTD uvc_compat.h
341c341
< #if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,28)
---
> #if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,26)


This suppresses the last paragraph of uvc_compat.h, removing the redundant definition of video_drvdata. There is, no doubt, a more correct way to fix this, but hey, this works.

---

### Post by complete n00b on 2008-12-30
Hi, can anybody tell me how to switch from the uvcvideo driver to the stk11xx driver? I haven't been able to get these patches to work, but apparently stk11xx driver has a vflip option which makes everything much simpler.

---

### Post by cslashm on 2009-01-11
Hi all, 

I experience some troubles in applying patch on Ubuntu8.10.
In  2.6.27 kernel, the uvc source driver is provided with kernel source, and i would like to use it.
Installing the package "linux-source" and "linux-headers-2.6.27-9-generic", the source is located in :
/usr/src/linux-source-2.6.27/drivers/media/video/uvc

So I applied the patch (solution 2, not Mirrored) by hand, to this source.
Then I follow the following procedure.

#get the kernel version
uname -a

"Linux margouillat 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux"

#copy the kernel config file into the kernel source
 cd /usr/src/linux-source-2.6.27
 cp /boot/config-2.6.27-9-generic .config

#edit the Makefile (not sure it is necessary) and fix the follwing line:
EXTRAVERSION = -9-generic

#rebuild the module
 make drivers/media/video/uvc/uvcvideo.ko

#install module
 cp drivers/media/video/uvc/uvcvideo.ko /lib/modules/2.6.27-9-generic/kernel/drivers/media/video/uvc/uvcvideo.ko

#load module
rmmod uvcvideo
modprob uvcvideo

At this point, he modprob failed with the message:
insmod /lib/modules/2.6.27-9-generic/kernel/drivers/media/video/uvc/uvcvideo.ko 
FATAL: Error inserting uvcvideo (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/uvc/uvcvideo.ko): Invalid module format

A dmesg gives the following info:
Jan 11 19:01:36 margouillat kernel: [26912.386709] uvcvideo: no symbol version for struct_module

I also tried with original source (just in case), but the problem remains.

(Note: if you try that, take care to keep a copy of your orignal uvcvideo.ko ;) )


I googled a lot, but didnot found any solution. I certainly missed something in howto to rebuild a module for ubuntu kernel.
Thanks for your help

C/M.

---

### Post by cslashm on 2009-01-15
Hil all,

I finally resolved my problem.
After getting the problem from scratch and googling around kernel compilation and module compilation I found my error.
kernel was compiled with CONFIG_MODVERSION=y, so a full kernel
compilation is necessary.
> make
> make modules

Now the module seems correctly loaded. I've not yet tested it (other thing to do before with the Ricoch driver before), I hope it will be ok. I will post again (this WE certainly), once all work correctly, and will give some details on my config
(ubuntu/VAIO FZ11S). It may help some people ;)

Many thanks arjos85 for your initial post.

C/M.

---

### Post by romo1987 on 2009-01-18
Not working for me... any of the solutions

My laptop is a Packard Bell Easynote BG46-T, the webcam is a Chicony Electronics USB2.0 1.3M UVC Webcam...

any idea? :(

---

### Post by kubumar on 2009-02-28
Hi,

I always get a

/isoft/trunk$ patch < uvc_video_solution1.patch
patching file uvc_video.c
Hunk #1 FAILED at 371.
1 out of 1 hunk FAILED -- saving rejects to file uvc_video.c.rej

when trying to patch. I know it has to do with the blank line, which has to be added to the code....I did it with kate but it doesn't seems to work. 

PLEASE can someone tell me how to add the blank line correctly?

greets
kubumar

---

### Post by kubumar on 2009-03-01
anyone there who can help me?

:(:(

---

### Post by kubumar on 2009-03-02
:guitar::guitar:

Finally everything works!

How:
In Kate, I actually had to add TWO empty lines to make the patch work.

Then: To install the patched file I followed the steps as cslashm described.
      Only difference: I had no error after "modprobe uvcvideo". Everything 
      works fine now.

My System: Sony Vaio FZ11S, Kubuntu 8.10 Kernel 2.6.27-7-generic

Thanks to clashm and of course arjos85 !

---

### Post by art_s on 2009-03-02
Hi all,

I noticed that when you're trying to build the patched driver it says:

> -------------------------------- WARNING ---------------------------------------
 The USB Video Class driver has moved to [http://linuxtv.org/](http://linuxtv.org/).
 Using the Berlios SVN repository is now deprecated.
 Please check [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) for download instructions.
 If you really want to compile this historical version, run 'make uvcvideo'.
--------------------------------------------------------------------------------


So I wonder did anyone try to do this with version from [http://linuxtv.org/](http://linuxtv.org/) 
?

Thanks!

---

### Post by iliev on 2009-03-02
Everything works fine for me with patch_solution2_mirrored.txt on ASUS U6V Bamboo. Camera is 0.3M: Bus 008 Device 003: ID 04f2:b036 Chicony Electronics Co., Ltd

---

### Post by paul111 on 2009-03-10
hi, well it's my first laptop and i just installed ubuntu 8.10 linux for the first time so i'm not familiar with most commands nor the workings of this os, so far everything works fine with everything except the web-cam.

i have a packard bell easy note bg45 u 300 and since the image appeared upside down i bluntly applied these commands i found in the forum 

Try this steps:
```
sudo find /lib/modules/ -name uvcvideo.ko  (give me the output)
sudo modprobe -r uvcvideo
sudo rm `find /lib/modules/2.6.24-19-generic/ -name uvcvideo.ko`
sudo make install
sudo cp uvcvideo.ko /lib/modules/2.6.24-19-generic/usb/media/
sudo depmod -ae
sudo modprobe -f uvcvideo
```Let me know,
thank  you!!

Regards,

arjos85[/QUOTE]

but it seems i only eliminated module but couldn't do the make install part now it doesn't recognize the camera at all.
i tried down downloading uvcvideo-5ba3bf58b52d and added the modules i removed but still no camera, please help

if its of use:
Bus 007 Device 002: ID 04f2:b012 Chicony Electronics Co., Ltd 1.3 MPixel UVC webcam
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

*_*

---

### Post by m121212 on 2009-03-18
I had this fixed using the patch.  After some time, ubuntu had several automatic updates, one of which upgrade the kernel to a version which included uvcvideo in the kernel.

Now I'm not sure what to do.   Is there any chance I can just change some setting to flip the video without doing any compiling or kernel hacking?  I don't want to have to patch and recompile things all the time; it's really convenient to just use the generic kernel. 

If it's not possible, how do we apply the fix for the module when it's built into the kernel?

Thanks,
m121212

---

### Post by mertyamak on 2009-03-28
make returns 2 errors in jaunty 9.04 beta. Any help please ?

---

### Post by Regel on 2009-03-29
Same problem, make returns errors, worked in intrepid.

---

### Post by bekirserifoglu on 2009-03-29
> **mertyamak said:**
> make returns 2 errors in jaunty 9.04 beta. Any help please ?

since uvc_v4l2 has changed in kernel 2.6.28, make gives errors. you need to use file uvc_v4l2.c from kernel source instead of the one from uvc trunk. you can get it from the kernel source. I am attaching a copy of that to make it easier for you. do not forget to change file extension from txt to c. just replace uvc_v4l2.c with the one attached to the post and try to compile again. 

the file size exceeds the forum's limit. so here is the code itself. save it as v4l2.c and put a blank line at the end of the file. 

```
/*
 *      uvc_v4l2.c  --  USB Video Class driver - V4L2 API
 *
 *      Copyright (C) 2005-2008
 *          Laurent Pinchart (laurent.pinchart@skynet.be)
 *
 *      This program is free software; you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation; either version 2 of the License, or
 *      (at your option) any later version.
 *
 */

#include <linux/kernel.h>
#include <linux/version.h>
#include <linux/list.h>
#include <linux/module.h>
#include <linux/usb.h>
#include <linux/videodev2.h>
#include <linux/vmalloc.h>
#include <linux/mm.h>
#include <linux/wait.h>
#include <asm/atomic.h>

#include <media/v4l2-common.h>
#include <media/v4l2-ioctl.h>

#include "uvcvideo.h"

/* ------------------------------------------------------------------------
 * V4L2 interface
 */

/*
 * Mapping V4L2 controls to UVC controls can be straighforward if done well.
 * Most of the UVC controls exist in V4L2, and can be mapped directly. Some
 * must be grouped (for instance the Red Balance, Blue Balance and Do White
 * Balance V4L2 controls use the White Balance Component UVC control) or
 * otherwise translated. The approach we take here is to use a translation
 * table for the controls which can be mapped directly, and handle the others
 * manually.
 */
static int uvc_v4l2_query_menu(struct uvc_video_device *video,
	struct v4l2_querymenu *query_menu)
{
	struct uvc_menu_info *menu_info;
	struct uvc_control_mapping *mapping;
	struct uvc_control *ctrl;

	ctrl = uvc_find_control(video, query_menu->id, &mapping);
	if (ctrl == NULL || mapping->v4l2_type != V4L2_CTRL_TYPE_MENU)
		return -EINVAL;

	if (query_menu->index >= mapping->menu_count)
		return -EINVAL;

	menu_info = &mapping->menu_info[query_menu->index];
	strncpy(query_menu->name, menu_info->name, 32);
	return 0;
}

/*
 * Find the frame interval closest to the requested frame interval for the
 * given frame format and size. This should be done by the device as part of
 * the Video Probe and Commit negotiation, but some hardware don't implement
 * that feature.
 */
static __u32 uvc_try_frame_interval(struct uvc_frame *frame, __u32 interval)
{
	unsigned int i;

	if (frame->bFrameIntervalType) {
		__u32 best = -1, dist;

		for (i = 0; i < frame->bFrameIntervalType; ++i) {
			dist = interval > frame->dwFrameInterval[i]
			     ? interval - frame->dwFrameInterval[i]
			     : frame->dwFrameInterval[i] - interval;

			if (dist > best)
				break;

			best = dist;
		}

		interval = frame->dwFrameInterval[i-1];
	} else {
		const __u32 min = frame->dwFrameInterval[0];
		const __u32 max = frame->dwFrameInterval[1];
		const __u32 step = frame->dwFrameInterval[2];

		interval = min + (interval - min + step/2) / step * step;
		if (interval > max)
			interval = max;
	}

	return interval;
}

static int uvc_v4l2_try_format(struct uvc_video_device *video,
	struct v4l2_format *fmt, struct uvc_streaming_control *probe,
	struct uvc_format **uvc_format, struct uvc_frame **uvc_frame)
{
	struct uvc_format *format = NULL;
	struct uvc_frame *frame = NULL;
	__u16 rw, rh;
	unsigned int d, maxd;
	unsigned int i;
	__u32 interval;
	int ret = 0;
	__u8 *fcc;

	if (fmt->type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
		return -EINVAL;

	fcc = (__u8 *)&fmt->fmt.pix.pixelformat;
	uvc_trace(UVC_TRACE_FORMAT, "Trying format 0x%08x (%c%c%c%c): %ux%u.\n",
			fmt->fmt.pix.pixelformat,
			fcc[0], fcc[1], fcc[2], fcc[3],
			fmt->fmt.pix.width, fmt->fmt.pix.height);

	/* Check if the hardware supports the requested format. */
	for (i = 0; i < video->streaming->nformats; ++i) {
		format = &video->streaming->format[i];
		if (format->fcc == fmt->fmt.pix.pixelformat)
			break;
	}

	if (format == NULL || format->fcc != fmt->fmt.pix.pixelformat) {
		uvc_trace(UVC_TRACE_FORMAT, "Unsupported format 0x%08x.\n",
				fmt->fmt.pix.pixelformat);
		return -EINVAL;
	}

	/* Find the closest image size. The distance between image sizes is
	 * the size in pixels of the non-overlapping regions between the
	 * requested size and the frame-specified size.
	 */
	rw = fmt->fmt.pix.width;
	rh = fmt->fmt.pix.height;
	maxd = (unsigned int)-1;

	for (i = 0; i < format->nframes; ++i) {
		__u16 w = format->frame[i].wWidth;
		__u16 h = format->frame[i].wHeight;

		d = min(w, rw) * min(h, rh);
		d = w*h + rw*rh - 2*d;
		if (d < maxd) {
			maxd = d;
			frame = &format->frame[i];
		}

		if (maxd == 0)
			break;
	}

	if (frame == NULL) {
		uvc_trace(UVC_TRACE_FORMAT, "Unsupported size %ux%u.\n",
				fmt->fmt.pix.width, fmt->fmt.pix.height);
		return -EINVAL;
	}

	/* Use the default frame interval. */
	interval = frame->dwDefaultFrameInterval;
	uvc_trace(UVC_TRACE_FORMAT, "Using default frame interval %u.%u us "
		"(%u.%u fps).\n", interval/10, interval%10, 10000000/interval,
		(100000000/interval)%10);

	/* Set the format index, frame index and frame interval. */
	memset(probe, 0, sizeof *probe);
	probe->bmHint = 1;	/* dwFrameInterval */
	probe->bFormatIndex = format->index;
	probe->bFrameIndex = frame->bFrameIndex;
	probe->dwFrameInterval = uvc_try_frame_interval(frame, interval);
	/* Some webcams stall the probe control set request when the
	 * dwMaxVideoFrameSize field is set to zero. The UVC specification
	 * clearly states that the field is read-only from the host, so this
	 * is a webcam bug. Set dwMaxVideoFrameSize to the value reported by
	 * the webcam to work around the problem.
	 *
	 * The workaround could probably be enabled for all webcams, so the
	 * quirk can be removed if needed. It's currently useful to detect
	 * webcam bugs and fix them before they hit the market (providing
	 * developers test their webcams with the Linux driver as well as with
	 * the Windows driver).
	 */
	if (video->dev->quirks & UVC_QUIRK_PROBE_EXTRAFIELDS)
		probe->dwMaxVideoFrameSize =
			video->streaming->ctrl.dwMaxVideoFrameSize;

	/* Probe the device */
	if ((ret = uvc_probe_video(video, probe)) < 0)
		goto done;

	fmt->fmt.pix.width = frame->wWidth;
	fmt->fmt.pix.height = frame->wHeight;
	fmt->fmt.pix.field = V4L2_FIELD_NONE;
	fmt->fmt.pix.bytesperline = format->bpp * frame->wWidth / 8;
	fmt->fmt.pix.sizeimage = probe->dwMaxVideoFrameSize;
	fmt->fmt.pix.colorspace = format->colorspace;
	fmt->fmt.pix.priv = 0;

	if (uvc_format != NULL)
		*uvc_format = format;
	if (uvc_frame != NULL)
		*uvc_frame = frame;

done:
	return ret;
}

static int uvc_v4l2_get_format(struct uvc_video_device *video,
	struct v4l2_format *fmt)
{
	struct uvc_format *format = video->streaming->cur_format;
	struct uvc_frame *frame = video->streaming->cur_frame;

	if (fmt->type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
		return -EINVAL;

	if (format == NULL || frame == NULL)
		return -EINVAL;

	fmt->fmt.pix.pixelformat = format->fcc;
	fmt->fmt.pix.width = frame->wWidth;
	fmt->fmt.pix.height = frame->wHeight;
	fmt->fmt.pix.field = V4L2_FIELD_NONE;
	fmt->fmt.pix.bytesperline = format->bpp * frame->wWidth / 8;
	fmt->fmt.pix.sizeimage = video->streaming->ctrl.dwMaxVideoFrameSize;
	fmt->fmt.pix.colorspace = format->colorspace;
	fmt->fmt.pix.priv = 0;

	return 0;
}

static int uvc_v4l2_set_format(struct uvc_video_device *video,
	struct v4l2_format *fmt)
{
	struct uvc_streaming_control probe;
	struct uvc_format *format;
	struct uvc_frame *frame;
	int ret;

	if (fmt->type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
		return -EINVAL;

	if (uvc_queue_streaming(&video->queue))
		return -EBUSY;

	ret = uvc_v4l2_try_format(video, fmt, &probe, &format, &frame);
	if (ret < 0)
		return ret;

	memcpy(&video->streaming->ctrl, &probe, sizeof probe);
	video->streaming->cur_format = format;
	video->streaming->cur_frame = frame;

	return 0;
}

static int uvc_v4l2_get_streamparm(struct uvc_video_device *video,
		struct v4l2_streamparm *parm)
{
	uint32_t numerator, denominator;

	if (parm->type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
		return -EINVAL;

	numerator = video->streaming->ctrl.dwFrameInterval;
	denominator = 10000000;
	uvc_simplify_fraction(&numerator, &denominator, 8, 333);

	memset(parm, 0, sizeof *parm);
	parm->type = V4L2_BUF_TYPE_VIDEO_CAPTURE;
	parm->parm.capture.capability = V4L2_CAP_TIMEPERFRAME;
	parm->parm.capture.capturemode = 0;
	parm->parm.capture.timeperframe.numerator = numerator;
	parm->parm.capture.timeperframe.denominator = denominator;
	parm->parm.capture.extendedmode = 0;
	parm->parm.capture.readbuffers = 0;

	return 0;
}

static int uvc_v4l2_set_streamparm(struct uvc_video_device *video,
		struct v4l2_streamparm *parm)
{
	struct uvc_frame *frame = video->streaming->cur_frame;
	struct uvc_streaming_control probe;
	uint32_t interval;
	int ret;

	if (parm->type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
		return -EINVAL;

	if (uvc_queue_streaming(&video->queue))
		return -EBUSY;

	memcpy(&probe, &video->streaming->ctrl, sizeof probe);
	interval = uvc_fraction_to_interval(
			parm->parm.capture.timeperframe.numerator,
			parm->parm.capture.timeperframe.denominator);

	uvc_trace(UVC_TRACE_FORMAT, "Setting frame interval to %u/%u (%u).\n",
			parm->parm.capture.timeperframe.numerator,
			parm->parm.capture.timeperframe.denominator,
			interval);
	probe.dwFrameInterval = uvc_try_frame_interval(frame, interval);

	/* Probe the device with the new settings. */
	if ((ret = uvc_probe_video(video, &probe)) < 0)
		return ret;

	memcpy(&video->streaming->ctrl, &probe, sizeof probe);

	/* Return the actual frame period. */
	parm->parm.capture.timeperframe.numerator = probe.dwFrameInterval;
	parm->parm.capture.timeperframe.denominator = 10000000;
	uvc_simplify_fraction(&parm->parm.capture.timeperframe.numerator,
				&parm->parm.capture.timeperframe.denominator,
				8, 333);

	return 0;
}

/* ------------------------------------------------------------------------
 * Privilege management
 */

/*
 * Privilege management is the multiple-open implementation basis. The current
 * implementation is completely transparent for the end-user and doesn't
 * require explicit use of the VIDIOC_G_PRIORITY and VIDIOC_S_PRIORITY ioctls.
 * Those ioctls enable finer control on the device (by making possible for a
 * user to request exclusive access to a device), but are not mature yet.
 * Switching to the V4L2 priority mechanism might be considered in the future
 * if this situation changes.
 *
 * Each open instance of a UVC device can either be in a privileged or
 * unprivileged state. Only a single instance can be in a privileged state at
 * a given time. Trying to perform an operation which requires privileges will
 * automatically acquire the required privileges if possible, or return -EBUSY
 * otherwise. Privileges are dismissed when closing the instance.
 *
 * Operations which require privileges are:
 *
 * - VIDIOC_S_INPUT
 * - VIDIOC_S_PARM
 * - VIDIOC_S_FMT
 * - VIDIOC_TRY_FMT
 * - VIDIOC_REQBUFS
 */
static int uvc_acquire_privileges(struct uvc_fh *handle)
{
	int ret = 0;

	/* Always succeed if the handle is already privileged. */
	if (handle->state == UVC_HANDLE_ACTIVE)
		return 0;

	/* Check if the device already has a privileged handle. */
	mutex_lock(&uvc_driver.open_mutex);
	if (atomic_inc_return(&handle->device->active) != 1) {
		atomic_dec(&handle->device->active);
		ret = -EBUSY;
		goto done;
	}

	handle->state = UVC_HANDLE_ACTIVE;

done:
	mutex_unlock(&uvc_driver.open_mutex);
	return ret;
}

static void uvc_dismiss_privileges(struct uvc_fh *handle)
{
	if (handle->state == UVC_HANDLE_ACTIVE)
		atomic_dec(&handle->device->active);

	handle->state = UVC_HANDLE_PASSIVE;
}

static int uvc_has_privileges(struct uvc_fh *handle)
{
	return handle->state == UVC_HANDLE_ACTIVE;
}

/* ------------------------------------------------------------------------
 * V4L2 file operations
 */

static int uvc_v4l2_open(struct inode *inode, struct file *file)
{
	struct uvc_video_device *video;
	struct uvc_fh *handle;
	int ret = 0;

	uvc_trace(UVC_TRACE_CALLS, "uvc_v4l2_open\n");
	mutex_lock(&uvc_driver.open_mutex);
	video = video_drvdata(file);

	if (video->dev->state & UVC_DEV_DISCONNECTED) {
		ret = -ENODEV;
		goto done;
	}

	ret = usb_autopm_get_interface(video->dev->intf);
	if (ret < 0)
		goto done;

	/* Create the device handle. */
	handle = kzalloc(sizeof *handle, GFP_KERNEL);
	if (handle == NULL) {
		usb_autopm_put_interface(video->dev->intf);
		ret = -ENOMEM;
		goto done;
	}

	handle->device = video;
	handle->state = UVC_HANDLE_PASSIVE;
	file->private_data = handle;

	kref_get(&video->dev->kref);

done:
	mutex_unlock(&uvc_driver.open_mutex);
	return ret;
}

static int uvc_v4l2_release(struct inode *inode, struct file *file)
{
	struct uvc_video_device *video = video_drvdata(file);
	struct uvc_fh *handle = (struct uvc_fh *)file->private_data;

	uvc_trace(UVC_TRACE_CALLS, "uvc_v4l2_release\n");

	/* Only free resources if this is a privileged handle. */
	if (uvc_has_privileges(handle)) {
		uvc_video_enable(video, 0);

		mutex_lock(&video->queue.mutex);
		if (uvc_free_buffers(&video->queue) < 0)
			uvc_printk(KERN_ERR, "uvc_v4l2_release: Unable to "
					"free buffers.\n");
		mutex_unlock(&video->queue.mutex);
	}

	/* Release the file handle. */
	uvc_dismiss_privileges(handle);
	kfree(handle);
	file->private_data = NULL;

	usb_autopm_put_interface(video->dev->intf);
	kref_put(&video->dev->kref, uvc_delete);
	return 0;
}

static int __uvc_v4l2_do_ioctl(struct file *file,
		     unsigned int cmd, void *arg)
{
	struct video_device *vdev = video_devdata(file);
	struct uvc_video_device *video = video_get_drvdata(vdev);
	struct uvc_fh *handle = (struct uvc_fh *)file->private_data;
	int ret = 0;

	if (uvc_trace_param & UVC_TRACE_IOCTL)
		v4l_printk_ioctl(cmd);

	switch (cmd) {
	/* Query capabilities */
	case VIDIOC_QUERYCAP:
	{
		struct v4l2_capability *cap = arg;

		memset(cap, 0, sizeof *cap);
		strncpy(cap->driver, "uvcvideo", sizeof cap->driver);
		strncpy(cap->card, vdev->name, 32);
		strncpy(cap->bus_info, video->dev->udev->bus->bus_name,
			sizeof cap->bus_info);
		cap->version = DRIVER_VERSION_NUMBER;
		cap->capabilities = V4L2_CAP_VIDEO_CAPTURE
				  | V4L2_CAP_STREAMING;
		break;
	}

	/* Get, Set & Query control */
	case VIDIOC_QUERYCTRL:
		return uvc_query_v4l2_ctrl(video, arg);

	case VIDIOC_G_CTRL:
	{
		struct v4l2_control *ctrl = arg;
		struct v4l2_ext_control xctrl;

		memset(&xctrl, 0, sizeof xctrl);
		xctrl.id = ctrl->id;

		uvc_ctrl_begin(video);
		ret = uvc_ctrl_get(video, &xctrl);
		uvc_ctrl_rollback(video);
		if (ret >= 0)
			ctrl->value = xctrl.value;
		break;
	}

	case VIDIOC_S_CTRL:
	{
		struct v4l2_control *ctrl = arg;
		struct v4l2_ext_control xctrl;

		memset(&xctrl, 0, sizeof xctrl);
		xctrl.id = ctrl->id;
		xctrl.value = ctrl->value;

		uvc_ctrl_begin(video);
		ret = uvc_ctrl_set(video, &xctrl);
		if (ret < 0) {
			uvc_ctrl_rollback(video);
			return ret;
		}
		ret = uvc_ctrl_commit(video);
		break;
	}

	case VIDIOC_QUERYMENU:
		return uvc_v4l2_query_menu(video, arg);

	case VIDIOC_G_EXT_CTRLS:
	{
		struct v4l2_ext_controls *ctrls = arg;
		struct v4l2_ext_control *ctrl = ctrls->controls;
		unsigned int i;

		uvc_ctrl_begin(video);
		for (i = 0; i < ctrls->count; ++ctrl, ++i) {
			ret = uvc_ctrl_get(video, ctrl);
			if (ret < 0) {
				uvc_ctrl_rollback(video);
				ctrls->error_idx = i;
				return ret;
			}
		}
		ctrls->error_idx = 0;
		ret = uvc_ctrl_rollback(video);
		break;
	}

	case VIDIOC_S_EXT_CTRLS:
	case VIDIOC_TRY_EXT_CTRLS:
	{
		struct v4l2_ext_controls *ctrls = arg;
		struct v4l2_ext_control *ctrl = ctrls->controls;
		unsigned int i;

		ret = uvc_ctrl_begin(video);
		if (ret < 0)
			return ret;

		for (i = 0; i < ctrls->count; ++ctrl, ++i) {
			ret = uvc_ctrl_set(video, ctrl);
			if (ret < 0) {
				uvc_ctrl_rollback(video);
				ctrls->error_idx = i;
				return ret;
			}
		}

		ctrls->error_idx = 0;

		if (cmd == VIDIOC_S_EXT_CTRLS)
			ret = uvc_ctrl_commit(video);
		else
			ret = uvc_ctrl_rollback(video);
		break;
	}

	/* Get, Set & Enum input */
	case VIDIOC_ENUMINPUT:
	{
		const struct uvc_entity *selector = video->selector;
		struct v4l2_input *input = arg;
		struct uvc_entity *iterm = NULL;
		u32 index = input->index;
		int pin = 0;

		if (selector == NULL ||
		    (video->dev->quirks & UVC_QUIRK_IGNORE_SELECTOR_UNIT)) {
			if (index != 0)
				return -EINVAL;
			iterm = list_first_entry(&video->iterms,
					struct uvc_entity, chain);
			pin = iterm->id;
		} else if (pin < selector->selector.bNrInPins) {
			pin = selector->selector.baSourceID[index];
			list_for_each_entry(iterm, video->iterms.next, chain) {
				if (iterm->id == pin)
					break;
			}
		}

		if (iterm == NULL || iterm->id != pin)
			return -EINVAL;

		memset(input, 0, sizeof *input);
		input->index = index;
		strncpy(input->name, iterm->name, sizeof input->name);
		if (UVC_ENTITY_TYPE(iterm) == ITT_CAMERA)
			input->type = V4L2_INPUT_TYPE_CAMERA;
		break;
	}

	case VIDIOC_G_INPUT:
	{
		u8 input;

		if (video->selector == NULL ||
		    (video->dev->quirks & UVC_QUIRK_IGNORE_SELECTOR_UNIT)) {
			*(int *)arg = 0;
			break;
		}

		ret = uvc_query_ctrl(video->dev, GET_CUR, video->selector->id,
			video->dev->intfnum, SU_INPUT_SELECT_CONTROL,
			&input, 1);
		if (ret < 0)
			return ret;

		*(int *)arg = input - 1;
		break;
	}

	case VIDIOC_S_INPUT:
	{
		u8 input = *(u32 *)arg + 1;

		if ((ret = uvc_acquire_privileges(handle)) < 0)
			return ret;

		if (video->selector == NULL ||
		    (video->dev->quirks & UVC_QUIRK_IGNORE_SELECTOR_UNIT)) {
			if (input != 1)
				return -EINVAL;
			break;
		}

		if (input > video->selector->selector.bNrInPins)
			return -EINVAL;

		return uvc_query_ctrl(video->dev, SET_CUR, video->selector->id,
			video->dev->intfnum, SU_INPUT_SELECT_CONTROL,
			&input, 1);
	}

	/* Try, Get, Set & Enum format */
	case VIDIOC_ENUM_FMT:
	{
		struct v4l2_fmtdesc *fmt = arg;
		struct uvc_format *format;

		if (fmt->type != V4L2_BUF_TYPE_VIDEO_CAPTURE ||
		    fmt->index >= video->streaming->nformats)
			return -EINVAL;

		format = &video->streaming->format[fmt->index];
		fmt->flags = 0;
		if (format->flags & UVC_FMT_FLAG_COMPRESSED)
			fmt->flags |= V4L2_FMT_FLAG_COMPRESSED;
		strncpy(fmt->description, format->name,
			sizeof fmt->description);
		fmt->description[sizeof fmt->description - 1] = 0;
		fmt->pixelformat = format->fcc;
		break;
	}

	case VIDIOC_TRY_FMT:
	{
		struct uvc_streaming_control probe;

		if ((ret = uvc_acquire_privileges(handle)) < 0)
			return ret;

		return uvc_v4l2_try_format(video, arg, &probe, NULL, NULL);
	}

	case VIDIOC_S_FMT:
		if ((ret = uvc_acquire_privileges(handle)) < 0)
			return ret;

		return uvc_v4l2_set_format(video, arg);

	case VIDIOC_G_FMT:
		return uvc_v4l2_get_format(video, arg);

	/* Frame size enumeration */
	case VIDIOC_ENUM_FRAMESIZES:
	{
		struct v4l2_frmsizeenum *fsize = arg;
		struct uvc_format *format = NULL;
		struct uvc_frame *frame;
		int i;

		/* Look for the given pixel format */
		for (i = 0; i < video->streaming->nformats; i++) {
			if (video->streaming->format[i].fcc ==
					fsize->pixel_format) {
				format = &video->streaming->format[i];
				break;
			}
		}
		if (format == NULL)
			return -EINVAL;

		if (fsize->index >= format->nframes)
			return -EINVAL;

		frame = &format->frame[fsize->index];
		fsize->type = V4L2_FRMSIZE_TYPE_DISCRETE;
		fsize->discrete.width = frame->wWidth;
		fsize->discrete.height = frame->wHeight;
		break;
	}

	/* Frame interval enumeration */
	case VIDIOC_ENUM_FRAMEINTERVALS:
	{
		struct v4l2_frmivalenum *fival = arg;
		struct uvc_format *format = NULL;
		struct uvc_frame *frame = NULL;
		int i;

		/* Look for the given pixel format and frame size */
		for (i = 0; i < video->streaming->nformats; i++) {
			if (video->streaming->format[i].fcc ==
					fival->pixel_format) {
				format = &video->streaming->format[i];
				break;
			}
		}
		if (format == NULL)
			return -EINVAL;

		for (i = 0; i < format->nframes; i++) {
			if (format->frame[i].wWidth == fival->width &&
			    format->frame[i].wHeight == fival->height) {
				frame = &format->frame[i];
				break;
			}
		}
		if (frame == NULL)
			return -EINVAL;

		if (frame->bFrameIntervalType) {
			if (fival->index >= frame->bFrameIntervalType)
				return -EINVAL;

			fival->type = V4L2_FRMIVAL_TYPE_DISCRETE;
			fival->discrete.numerator =
				frame->dwFrameInterval[fival->index];
			fival->discrete.denominator = 10000000;
			uvc_simplify_fraction(&fival->discrete.numerator,
				&fival->discrete.denominator, 8, 333);
		} else {
			fival->type = V4L2_FRMIVAL_TYPE_STEPWISE;
			fival->stepwise.min.numerator =
				frame->dwFrameInterval[0];
			fival->stepwise.min.denominator = 10000000;
			fival->stepwise.max.numerator =
				frame->dwFrameInterval[1];
			fival->stepwise.max.denominator = 10000000;
			fival->stepwise.step.numerator =
				frame->dwFrameInterval[2];
			fival->stepwise.step.denominator = 10000000;
			uvc_simplify_fraction(&fival->stepwise.min.numerator,
				&fival->stepwise.min.denominator, 8, 333);
			uvc_simplify_fraction(&fival->stepwise.max.numerator,
				&fival->stepwise.max.denominator, 8, 333);
			uvc_simplify_fraction(&fival->stepwise.step.numerator,
				&fival->stepwise.step.denominator, 8, 333);
		}
		break;
	}

	/* Get & Set streaming parameters */
	case VIDIOC_G_PARM:
		return uvc_v4l2_get_streamparm(video, arg);

	case VIDIOC_S_PARM:
		if ((ret = uvc_acquire_privileges(handle)) < 0)
			return ret;

		return uvc_v4l2_set_streamparm(video, arg);

	/* Cropping and scaling */
	case VIDIOC_CROPCAP:
	{
		struct v4l2_cropcap *ccap = arg;
		struct uvc_frame *frame = video->streaming->cur_frame;

		if (ccap->type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
			return -EINVAL;

		ccap->bounds.left = 0;
		ccap->bounds.top = 0;
		ccap->bounds.width = frame->wWidth;
		ccap->bounds.height = frame->wHeight;

		ccap->defrect = ccap->bounds;

		ccap->pixelaspect.numerator = 1;
		ccap->pixelaspect.denominator = 1;
		break;
	}

	case VIDIOC_G_CROP:
	case VIDIOC_S_CROP:
		return -EINVAL;

	/* Buffers & streaming */
	case VIDIOC_REQBUFS:
	{
		struct v4l2_requestbuffers *rb = arg;
		unsigned int bufsize =
			video->streaming->ctrl.dwMaxVideoFrameSize;

		if (rb->type != V4L2_BUF_TYPE_VIDEO_CAPTURE ||
		    rb->memory != V4L2_MEMORY_MMAP)
			return -EINVAL;

		if ((ret = uvc_acquire_privileges(handle)) < 0)
			return ret;

		ret = uvc_alloc_buffers(&video->queue, rb->count, bufsize);
		if (ret < 0)
			return ret;

		rb->count = ret;
		ret = 0;
		break;
	}

	case VIDIOC_QUERYBUF:
	{
		struct v4l2_buffer *buf = arg;

		if (buf->type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
			return -EINVAL;

		if (!uvc_has_privileges(handle))
			return -EBUSY;

		return uvc_query_buffer(&video->queue, buf);
	}

	case VIDIOC_QBUF:
		if (!uvc_has_privileges(handle))
			return -EBUSY;

		return uvc_queue_buffer(&video->queue, arg);

	case VIDIOC_DQBUF:
		if (!uvc_has_privileges(handle))
			return -EBUSY;

		return uvc_dequeue_buffer(&video->queue, arg,
			file->f_flags & O_NONBLOCK);

	case VIDIOC_STREAMON:
	{
		int *type = arg;

		if (*type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
			return -EINVAL;

		if (!uvc_has_privileges(handle))
			return -EBUSY;

		if ((ret = uvc_video_enable(video, 1)) < 0)
			return ret;
		break;
	}

	case VIDIOC_STREAMOFF:
	{
		int *type = arg;

		if (*type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
			return -EINVAL;

		if (!uvc_has_privileges(handle))
			return -EBUSY;

		return uvc_video_enable(video, 0);
	}

	/* Analog video standards make no sense for digital cameras. */
	case VIDIOC_ENUMSTD:
	case VIDIOC_QUERYSTD:
	case VIDIOC_G_STD:
	case VIDIOC_S_STD:

	case VIDIOC_OVERLAY:

	case VIDIOC_ENUMAUDIO:
	case VIDIOC_ENUMAUDOUT:

	case VIDIOC_ENUMOUTPUT:
		uvc_trace(UVC_TRACE_IOCTL, "Unsupported ioctl 0x%08x\n", cmd);
		return -EINVAL;

	/* Dynamic controls. */
	case UVCIOC_CTRL_ADD:
	{
		struct uvc_xu_control_info *xinfo = arg;
		struct uvc_control_info *info;

		if (!capable(CAP_SYS_ADMIN))
			return -EPERM;

		info = kmalloc(sizeof *info, GFP_KERNEL);
		if (info == NULL)
			return -ENOMEM;

		memcpy(info->entity, xinfo->entity, sizeof info->entity);
		info->index = xinfo->index;
		info->selector = xinfo->selector;
		info->size = xinfo->size;
		info->flags = xinfo->flags;

		info->flags |= UVC_CONTROL_GET_MIN | UVC_CONTROL_GET_MAX |
				UVC_CONTROL_GET_RES | UVC_CONTROL_GET_DEF;

		ret = uvc_ctrl_add_info(info);
		if (ret < 0)
			kfree(info);
		break;
	}

	case UVCIOC_CTRL_MAP:
	{
		struct uvc_xu_control_mapping *xmap = arg;
		struct uvc_control_mapping *map;

		if (!capable(CAP_SYS_ADMIN))
			return -EPERM;

		map = kmalloc(sizeof *map, GFP_KERNEL);
		if (map == NULL)
			return -ENOMEM;

		map->id = xmap->id;
		memcpy(map->name, xmap->name, sizeof map->name);
		memcpy(map->entity, xmap->entity, sizeof map->entity);
		map->selector = xmap->selector;
		map->size = xmap->size;
		map->offset = xmap->offset;
		map->v4l2_type = xmap->v4l2_type;
		map->data_type = xmap->data_type;

		ret = uvc_ctrl_add_mapping(map);
		if (ret < 0)
			kfree(map);
		break;
	}

	case UVCIOC_CTRL_GET:
		return uvc_xu_ctrl_query(video, arg, 0);

	case UVCIOC_CTRL_SET:
		return uvc_xu_ctrl_query(video, arg, 1);

	default:
		if ((ret = v4l_compat_translate_ioctl(file, cmd, arg,
			__uvc_v4l2_do_ioctl)) == -ENOIOCTLCMD)
			uvc_trace(UVC_TRACE_IOCTL, "Unknown ioctl 0x%08x\n",
				  cmd);
		return ret;
	}

	return ret;
}

static int uvc_v4l2_do_ioctl(struct inode *inode, struct file *file,
			      unsigned int cmd, void *arg)
{
	return __uvc_v4l2_do_ioctl(file, cmd, arg);
}

static int uvc_v4l2_ioctl(struct inode *inode, struct file *file,
		     unsigned int cmd, unsigned long arg)
{
	uvc_trace(UVC_TRACE_CALLS, "uvc_v4l2_ioctl\n");
	return video_usercopy(inode, file, cmd, arg, uvc_v4l2_do_ioctl);
}

static ssize_t uvc_v4l2_read(struct file *file, char __user *data,
		    size_t count, loff_t *ppos)
{
	uvc_trace(UVC_TRACE_CALLS, "uvc_v4l2_read: not implemented.\n");
	return -ENODEV;
}

/*
 * VMA operations.
 */
static void uvc_vm_open(struct vm_area_struct *vma)
{
	struct uvc_buffer *buffer = vma->vm_private_data;
	buffer->vma_use_count++;
}

static void uvc_vm_close(struct vm_area_struct *vma)
{
	struct uvc_buffer *buffer = vma->vm_private_data;
	buffer->vma_use_count--;
}

static struct vm_operations_struct uvc_vm_ops = {
	.open		= uvc_vm_open,
	.close		= uvc_vm_close,
};

static int uvc_v4l2_mmap(struct file *file, struct vm_area_struct *vma)
{
	struct uvc_video_device *video = video_drvdata(file);
	struct uvc_buffer *uninitialized_var(buffer);
	struct page *page;
	unsigned long addr, start, size;
	unsigned int i;
	int ret = 0;

	uvc_trace(UVC_TRACE_CALLS, "uvc_v4l2_mmap\n");

	start = vma->vm_start;
	size = vma->vm_end - vma->vm_start;

	mutex_lock(&video->queue.mutex);

	for (i = 0; i < video->queue.count; ++i) {
		buffer = &video->queue.buffer[i];
		if ((buffer->buf.m.offset >> PAGE_SHIFT) == vma->vm_pgoff)
			break;
	}

	if (i == video->queue.count || size != video->queue.buf_size) {
		ret = -EINVAL;
		goto done;
	}

	/*
	 * VM_IO marks the area as being an mmaped region for I/O to a
	 * device. It also prevents the region from being core dumped.
	 */
	vma->vm_flags |= VM_IO;

	addr = (unsigned long)video->queue.mem + buffer->buf.m.offset;
	while (size > 0) {
		page = vmalloc_to_page((void *)addr);
		if ((ret = vm_insert_page(vma, start, page)) < 0)
			goto done;

		start += PAGE_SIZE;
		addr += PAGE_SIZE;
		size -= PAGE_SIZE;
	}

	vma->vm_ops = &uvc_vm_ops;
	vma->vm_private_data = buffer;
	uvc_vm_open(vma);

done:
	mutex_unlock(&video->queue.mutex);
	return ret;
}

static unsigned int uvc_v4l2_poll(struct file *file, poll_table *wait)
{
	struct uvc_video_device *video = video_drvdata(file);

	uvc_trace(UVC_TRACE_CALLS, "uvc_v4l2_poll\n");

	return uvc_queue_poll(&video->queue, file, wait);
}

struct file_operations uvc_fops = {
	.owner		= THIS_MODULE,
	.open		= uvc_v4l2_open,
	.release	= uvc_v4l2_release,
	.ioctl		= uvc_v4l2_ioctl,
	.compat_ioctl	= v4l_compat_ioctl32,
	.llseek		= no_llseek,
	.read		= uvc_v4l2_read,
	.mmap		= uvc_v4l2_mmap,
	.poll		= uvc_v4l2_poll,
};


```

---

### Post by JimC111 on 2009-03-31
For Jaunty 9.04 beta (tested on 2.6.28-11-generic, but should work with 2.6.12 and later)

1) Download Linux UVC (not the obsolete ones from subversion!) from [http://linuxtv.org/repo/](http://linuxtv.org/repo/)
2) Modify v4l/uvc_video.c by hand according to instructions on the first post in this thread
3) Build and install UVC
```

make
sudo make install
sudo make unload
sudo modprobe uvcvideo

```

---

### Post by m121212 on 2009-04-09
That's fine if you're using the module. 

What about when using the built-in module for the generic kernel??

---

### Post by gupi-gupi on 2009-04-20
@JimC111 Thanks it worked well on my asus noteboock and jaunty with Syntek 1.3MPixel Web Cam - Asus G1s
toock a while to find the file to patch, I edit the path to make it easier for others:  patch < /v4l-dvb-74bd46cf88ee/linux/drivers/media/video/uvc/uvc_video.c
thanks to arjos85 as well!
:D

---

### Post by charlener on 2009-04-27
Above-mentioned instructions also worked for me on Jaunty netbook remix.

Question, though - last time I did a software update it seemed to have overwritten that module and I had to do the patch procedure again.  Any suggestions on how to disable/prevent automatic updates of that specific module?

---

### Post by art_s on 2009-04-27
> **JimC111 said:**
> For Jaunty 9.04 beta (tested on 2.6.28-11-generic, but should work with 2.6.12 and later)

Worked flawlessly for Jaunty, thanks!

Though I cannot help pointing out that situation with laptop uvc cameras is rather a depressing one. 

Why couldn't the driver support the 'vertical flip' parameter, as some other drivers do? 

Anyone annoyed enough with all these re-installations to suggest that to maintainers? :)

Anyhow, JimC111, thank you very much!

---

### Post by nhudan on 2009-04-28
> **tsl said:**
> Hi All,


I have an Asus U6S running Intrepid Ibex (kernel 2.6.27-7-generic).

From lsusb my webcam is a 04f2:b036 Chicony Electronics Co., Ltd 

Here is how I got my webcam working properly:

- sudo apt-get install subversion
- svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
patched the file with not mirrored patch #2
- make uvcvideo
- modified Makefile with the INSTALL_MOD_DIR := ubuntu/media/usbvideo
- sudo modprobe -r uvcvideo
- sudo make install
- sudo depmod -ae
- sudo modprobe uvcvideo

Everything working well!

Thanks!

Hello all!
Work for me too!

Thanks!

---

### Post by colossus_r on 2009-04-29
> **JimC111 said:**
> For Jaunty 9.04 beta (tested on 2.6.28-11-generic, but should work with 2.6.12 and later)

1) Download Linux UVC (not the obsolete ones from subversion!) from [http://linuxtv.org/repo/](http://linuxtv.org/repo/)
2) Modify v4l/uvc_video.c by hand according to instructions on the first post in this thread
3) Build and install UVC
```

make
sudo make install
sudo make unload
sudo modprobe uvcvideo

```

you say :

2. Modify the uvc_video.c by hand according to instructions on the first post in this thread......

How do i modify the file the you say here ???
In the first post are only paches ???
Those paches worked fine until 8.10 ...now on 9.04 the image is again upside down

my cam is:

Bus 002 Device 002: ID 04f2:b012 Chicony Electronics Co., Ltd 1.3 MPixel UVC webcam


Can someone please post the modified file here ????


colossus

---

### Post by dbkblk on 2009-05-03
I didn't understood neither :S

PS: I think you can modify the title to put [All Variants] instead of [Kubuntu] because it has nothing to do with KDE.

---

### Post by madias on 2009-05-09
same problem with errors with 9.04 - can`t follow the instructions, could somebody explain the steps for (k)ubuntu 9.04. my webcam is now broken :/

---

### Post by lasantarosa on 2009-05-11
Thanks so much for these patches, also work with kernel 2.6.30.

Should also work for normal ubuntu 9.04, just download the new uvcvideo from here and extract it:

[http://linuxtv.org/hg/~pinchartl/uvcvideo/](http://linuxtv.org/hg/~pinchartl/uvcvideo/)

e.g. tar xjvf uvcvideo.tar.bz2 if you got the bz2 archive.

Save the patch in the folder where you extracted uvcvideo to and change the path in the patch to:

linux/drivers/media/video/uvc/uvc_video.c

Then just execute

patch -p0 < patch_solution1_mirrored.txt

Should output that it patched it.

Now you can build the module with

make && make install

And load it with

modprobe uvcvideo

regards

---

### Post by rix-seu on 2009-05-16
Great solution. It worked on my netbook (asus n50vc series) and Ubuntu 9.04 (following last instructions of lasantarosa.

Thanks a lot.

---

### Post by Junx on 2009-05-19
Summary of steps that I can see:

```
sudo aptitude install mercurial
hg clone http://linuxtv.org/hg/~pinchartl/uvcvideo/
# wait like three hours it feels like
cd uvcvideo/linux/drivers/media/video/uvc/
patch < /path/to/patch_solution1_mirrored.txt
make
sudo make install
sudo make unload
sudo modprobe uvcvideo
```

Replacing the path/to/patchetc with the proper file.

Any improvements necessary? Should you avoid hg clone since it takes forever (unlike git hehe)?

---

### Post by snwbrdr464 on 2009-05-19
this is what worked for me:

first of all if you do not have the program mercurial installed you need that it uses hg to run so that's the program-name you would check:
aptitude install mercurial

then just do these in a terminal and it should work just fine:
hg clone [http://linuxtv.org/hg/~pinchartl/uvcvideo/](http://linuxtv.org/hg/~pinchartl/uvcvideo/)
cd uvcvideo/linux/drivers/media/video/uvc/
patch < ~/path/to/patch_solution1_mirrored.txt
cd ~/uvcvideo/
make
sudo make install
sudo make unload
sudo modprobe uvcvideo

good luck :D it wasn't too fun figuring this out junx helped quite a bit

---

### Post by dbzdeath on 2009-05-19
Hi,

This doesn't work for me properly. I've compiled and patched uvcvideo.

Method 1

With method 1 on resolutions at or below 176 x 144 this works fine, the image is displayed and it is up the correct way. If I go above 176 x 144(max for my cam is 1600 x 1200(according to cheese)) the cam window just remains black. I have tested with a couple of other programs and all seem to have the same result.

Method 2

Method 2 is the same as method 1 except that on the higher resolutions the picture is displayed but it is upside down(as it would be as if I never applied the patch)

Can anyone help me please?

Output of lsusb:

Bus 002 Device 002: ID 04f2:b106 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 147e:1000  
Bus 005 Device 002: ID 0b05:1751 ASUSTek Computer, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I'm using uvcvideo from [http://linuxtv.org/hg/~pinchartl/uvcvideo/](http://linuxtv.org/hg/~pinchartl/uvcvideo/)

---

### Post by com_h on 2009-05-28
Thanks for your watered down vers: snwbrdr464

Did it (word for word - copy and paste into terminal) on my ASUS N10J with 9.04 All working well.

Camera now the right way up and working in Skype & Cheese.

Thanks again,

com_h


> **snwbrdr464 said:**
> this is what worked for me:

first of all if you do not have the program mercurial installed you need that it uses hg to run so that's the program-name you would check:
aptitude install mercurial

then just do these in a terminal and it should work just fine:
hg clone [http://linuxtv.org/hg/~pinchartl/uvcvideo/]("http://linuxtv.org/hg/%7Epinchartl/uvcvideo/")
cd uvcvideo/linux/drivers/media/video/uvc/
patch < ~/path/to/patch_solution1_mirrored.txt
cd ~/uvcvideo/
make
sudo make install
sudo make unload
sudo modprobe uvcvideo

good luck :D it wasn't too fun figuring this out junx helped quite a bit

---

### Post by everdurm on 2009-05-30
Hi, 

I tried the solution as mentioned in this thread. A directory ~/trunk was made. After some struggling I ran the patch after downloaded the files from svn. I followed the instructions, .but I get the following error: 

sudo modprobe -f uvcvideo
FATAL: Module uvcvideo not found.
erwin@ubuntu:~/trunk$ sudo make install
Installing USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  DEPMOD  2.6.28-11-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
erwin@ubuntu:~/trunk$ sudo cp uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/
cp: cannot stat `uvcvideo.ko': No such file or directory
erwin@ubuntu:~/trunk$ sudo cp uvcvideo.ko /lib/modules/`uname -r`/usb/media/
cp: cannot stat `uvcvideo.ko': No such file or directory
erwin@ubuntu:~/trunk$ sudo depmod -ae
erwin@ubuntu:~/trunk$ sudo modprobe -f uvcvideo
FATAL: Module uvcvideo not found.

is there anybody who can help me? 

thanks, 
Erwin

---

### Post by xinix on 2009-06-02
None of the suggestions work for me.  They used to work on 8.04/10 but now they don't.  I have tried all the patches and the different methods suggested for 9.04. The patching works, building works, loading the module works. But, with patch 1 it still remains upside down.  With patch 2 I don't get a picture at all.  I've been testing with gstreamer-properties, [S]when I ran it in the terminal and tried it after patch 2 was applied[/S] I get this error in the terminal with all patches:

```
libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?
```

I have tried rebooting after each module (yes I know not needed cuz linux yada yada...).

I have an Asus N50vn,  I saw that the 'vc' version of this lappy was reported as working.  Must be a different camera.  In dmesg it identifies as a "CNF7246".

On a side note, in Expressgate (the Asus quick boot linux) the camera config app has a little check box to fix the problem.

---

### Post by xinix on 2009-06-02
Ok, so after spending a really long time trying to get various patches/svn versions of the driver. I have given up on a patched driver solution.  I have found something else that works (at least for my needs).

The solution is to use 'v4l2ucp' to configure the camera.  I've installed it from [[COLOR="SeaGreen"]here[/COLOR]]("https://launchpad.net/~stemp/+archive/ppa").  This app is a control panel that lets you change various settings; including horizontal and vertical flip.  I checked the vertical flip and the picture is oriented properly when testing with 'gstreamer-properties'.  It is not automatically flipped with 'skype'.  It works when it's launched with this command:
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

'luvcview' still gives me an upside down image and crashes if I try the preload command.

---

### Post by condowax on 2009-06-03
I tried the solution xinix suggested but I didn't get an option to flip the camera in v4lucp.

I'm running Ubuntu 9.04 and same laptop as xinix (Asus N50vn).

---

### Post by xinix on 2009-06-03
So you didn't have the options that are circled in the screenshot?  That's interesting,  I'm not sure what it could be.  I didn't think it made a difference but after adding the PPA for v4l2ucp I was notified of an update for libv4l-0.  Did you install that?

---

### Post by J-N-K on 2009-06-03
hi there. ive got the same error as [condowax]("http://ubuntuforums.org/member.php?u=519120"), v4l2ucp runs but there are no checkboxes to flip. i have jaunty jackalope on an asus b50a laptop.

in v4l2ucp it says version 1.3. which version did you download, xinix?

---

### Post by xinix on 2009-06-03
It's the one reported as 1.3.  I don't think I did anything special but here's what I did.
1, Got frustrated with compiling patched versions and re-installed the linux-image-2.6.28-11-generic.
2, Then added the PPA to my sources.list
3, Ran apt-get update & apt-get upgrade
   I was prompted to update libv4l-0, so I did.
4, I installed v4l2ucp via: apt-get install v4l2ucp
5, I ran v4l2ucp and got a window like the screenshot.
6, played with the flip options until I was happy with the picture.

I find it strange that I would have the option but others aren't seeing it, though not shocking since it is linux and drivers can be a pain (but not as much as it used to be).

---

### Post by condowax on 2009-06-04
Yes, there was an update pending for libv4l. After updating libv4l I got the check boxes in v4l2ucp. Thanks

---

### Post by .JNK on 2009-06-04
sorry to disturb again, but the problem is still there, there are no checkboxes to flip the picture in v4l2ucp. i tried deleting all the packages used by libv4l-0

```
jakob@jakob-laptop:~$ sudo apt-get remove libv4l-0 --purge
```and reinstalled all of them with

```
jakob@jakob-laptop:~$ sudo apt-get install [package-name]
```i also performed an update and upgrade with apt-get, without solving the problem. at first, the public keys for the ppa link had not been installed, but adding them and repeating all the steps above did not solve the problem either. i also reinstalled libv4l-0 many times using the synaptics-packet-manager, but it seems that the package is up to date as well as v4l2ucp itself. 

the package source is [http://ppa.launchpa.net/stemp/ppa/ubuntu](http://ppa.launchpa.net/stemp/ppa/ubuntu) jaunty main, isnt it?

any other ideas how to flip the picture without physically inverting the camera?
thanks for your help

---

### Post by xinix on 2009-06-04
.JNK
I'm not really sure what it could be.  I'm guessing that you have tried the patches to the uvcvideo module.  Did you re-install the driver that came with Ubuntu (you do this by re-installing linux-image)?
Otherwise, at least for now, I'm out of ideas on this one.

---

### Post by .JNK on 2009-06-05
yes, i reinstalled linux-image without effect. after reading in some forums, i think that using uvcvideo driver, there never will be any checkboxes to flip the image, because the parameter VFLIP is not implemented in the driver. but funny it works with your machine...

of course i tried the patches, but everytime i run the make-command, i get an error
```

jakob@jakob-laptop:~/trunk$ make
-------------------------------- WARNING ---------------------------------------
 The USB Video Class driver has moved to http://linuxtv.org/.
 Using the Berlios SVN repository is now deprecated.
 Please check http://linux-uvc.berlios.de/ for download instructions.
 If you really want to compile this historical version, run 'make uvcvideo'.
--------------------------------------------------------------------------------

```
if i then enter 
```

make uvcvideo

```
i end up with even more errors. anyone knows a solution for that?

---

### Post by xinix on 2009-06-05
Yes, read through this thread.  There are some posts that tell you how to do the building on a 9.04 setup. What camera is installed in your laptop?

While the driver itself may not support VFLIP.  The libv4l libraries are just a software layer in between the driver and the device.  So in theory you can have the image flipped for any app you want.  At least this is how I understand it works.

[[COLOR="DarkSlateBlue"]_http://hansdegoede.livejournal.com/3636.html_[/COLOR]]("http://hansdegoede.livejournal.com/3636.html")

---

### Post by .JNK on 2009-06-05
thank you xinix, at last i got the image flipped by downloading new sources and editing the function. so now the driver itself flips the image. but to figure out all this has cost me more than 20 hours - thats the bad thing about linux, everytime you have a problem you need so much time to get into the issue.
thanks anyway to everyone in this thread!

---

### Post by detlev24 on 2009-06-11
@.JNK: since i am new to ubuntu, could you please describe what exactly you did? thx!

---

### Post by HansdeGoede on 2009-06-19
Hi,

Short self intro: I've been a Linux developer for 10+ years now and lately
I'm working on improving support for webcams under Linux.

I'm the author of libv4l a userspace library for handling various v4l things in userspace, which is used by most applications now a days (in the last 2 ubuntu releases).

libv4l has the ability to put the image the right way up in software, and
is the right place to do this, unlike the patch in this thread which does
this inside the kernel. 

For this to work out of the box, libv4l needs to know that it is dealing
with an upside down webcam, for this I'm working on adding a table to libv4l with upside down cameras.

So I'm writing here in search of people with an upside down uvc webcam, and I would like to ask you some information about your camera (and notebook if its inside a notebook). If you have such a camera can you please run the following commands:
lsusb > usb.log
cat /sys/devices/virtual/dmi/id/board_name > name.txt
cat /sys/devices/virtual/dmi/id/board_vendor > vendor.txt

And *mail* me the output, it is important to attach the files to a mail
and not copy paste them here, as the name.txt and vendor.txt may very well
contain trailing whitespace which may get lost when copy pasted.

My mail address is: Hans de Goede <jwrdegoede@fedoraproject.org> .


p.s.

While I'm here, I'm also always looking for people with old unused webcams
to donate to my collection for testing (and bugfixing / improving drivers), see:
[http://fedoraproject.org/wiki/Features/BetterWebcamSupport#Test_Plan](http://fedoraproject.org/wiki/Features/BetterWebcamSupport#Test_Plan)

For a list of the camera's I already have.

---

### Post by kaladann on 2009-07-01
i trayed it but on make command i get some errors.

> uilding USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /dev/trunk/uvc_driver.o
  CC [M]  /dev/trunk/uvc_v4l2.o
/dev/trunk/uvc_v4l2.c: In function ‘uvc_v4l2_do_ioctl’:
/dev/trunk/uvc_v4l2.c:986: warning: passing argument 1 of ‘v4l_compat_translate_ioctl’ from incompatible pointer type
/dev/trunk/uvc_v4l2.c:986: warning: passing argument 2 of ‘v4l_compat_translate_ioctl’ makes integer from pointer without a cast
/dev/trunk/uvc_v4l2.c:986: warning: passing argument 3 of ‘v4l_compat_translate_ioctl’ makes pointer from integer without a cast
/dev/trunk/uvc_v4l2.c:986: error: too many arguments to function ‘v4l_compat_translate_ioctl’
make[2]: *** [/dev/trunk/uvc_v4l2.o] Error 1
make[1]: *** [_module_/dev/trunk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [uvcvideo] Error 2
root@dune:/dev/trunk#


---

### Post by rollcare on 2009-07-09
> **snwbrdr464 said:**
> this is what worked for me:

first of all if you do not have the program mercurial installed you need that it uses hg to run so that's the program-name you would check:
aptitude install mercurial

then just do these in a terminal and it should work just fine:
hg clone [http://linuxtv.org/hg/~pinchartl/uvcvideo/]("http://linuxtv.org/hg/%7Epinchartl/uvcvideo/")
cd uvcvideo/linux/drivers/media/video/uvc/
patch < ~/path/to/patch_solution1_mirrored.txt
cd ~/uvcvideo/
make
sudo make install
sudo make unload
sudo modprobe uvcvideo

good luck :D it wasn't too fun figuring this out junx helped quite a bit
thx bro.. u make me very happy.. this solved my problem for 2 weeks!!! thx dude..

i love ubuntu now!!

---

### Post by hannis on 2009-07-09
> **snwbrdr464 said:**
> this is what worked for me:

first of all if you do not have the program mercurial installed you need that it uses hg to run so that's the program-name you would check:
aptitude install mercurial

then just do these in a terminal and it should work just fine:
hg clone [http://linuxtv.org/hg/~pinchartl/uvcvideo/]("http://linuxtv.org/hg/%7Epinchartl/uvcvideo/")
cd uvcvideo/linux/drivers/media/video/uvc/
patch < ~/path/to/patch_solution1_mirrored.txt
cd ~/uvcvideo/
make
sudo make install
sudo make unload
sudo modprobe uvcvideo

good luck :D it wasn't too fun figuring this out junx helped quite a bit

This worked for me, too! Thanks a million. I found the "patch_solution1_mirrored.txt" file here: [http://ubuntuforums.org/attachment.php?attachmentid=75463&d=1214563240](http://ubuntuforums.org/attachment.php?attachmentid=75463&d=1214563240) .

---

### Post by pulsarunlimited on 2009-07-10
> **snwbrdr464 said:**
> this is what worked for me:

first of all if you do not have the program mercurial installed you need that it uses hg to run so that's the program-name you would check:
aptitude install mercurial

then just do these in a terminal and it should work just fine:
hg clone [http://linuxtv.org/hg/~pinchartl/uvcvideo/]("http://linuxtv.org/hg/%7Epinchartl/uvcvideo/")
cd uvcvideo/linux/drivers/media/video/uvc/
patch < ~/path/to/patch_solution1_mirrored.txt
cd ~/uvcvideo/
make
sudo make install
sudo make unload
sudo modprobe uvcvideo

good luck :D it wasn't too fun figuring this out junx helped quite a bit

[B]snwbrdr464, you da man!!!
This worked for me too. In skype anyway, which was the most important for me.

In Cheese webcam studio, the image is still upside down. Any ideas on why and how can fix that too? Anyone?

[/B]

---

### Post by Spoutniker on 2009-07-26
> [FONT=Arial][SIZE=2]**[COLOR=Red]You have to copy one of them into "Trunk" folder in a file (called for example "uvc_video_solution1.patch"), and then from terminal go into the "Trunk" folder and do:[/COLOR]**[/SIZE][/FONT]

What is the trunk folder?
How can I access to it from the terminal?
Thank you.

I'm new with linux (ubuntu) and I hope that I could use my Webcam.

---

### Post by kanishnish on 2009-07-27
> **Spoutniker said:**
> What is the trunk folder?
How can I access to it from the terminal?
Thank you.

I'm new with linux (ubuntu) and I hope that I could use my Webcam.


cd /home/yourname/trunk

or you can ~/trunk  

good day

---

### Post by PacShady on 2009-07-29
> **dbzdeath said:**
> Hi,

This doesn't work for me properly. I've compiled and patched uvcvideo.

Method 1

With method 1 on resolutions at or below 176 x 144 this works fine, the image is displayed and it is up the correct way. If I go above 176 x 144(max for my cam is 1600 x 1200(according to cheese)) the cam window just remains black. I have tested with a couple of other programs and all seem to have the same result.

Method 2

Method 2 is the same as method 1 except that on the higher resolutions the picture is displayed but it is upside down(as it would be as if I never applied the patch)

Can anyone help me please?

Output of lsusb:

Bus 002 Device 002: ID 04f2:b106 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 147e:1000  
Bus 005 Device 002: ID 0b05:1751 ASUSTek Computer, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I'm using uvcvideo from [http://linuxtv.org/hg/~pinchartl/uvcvideo/](http://linuxtv.org/hg/~pinchartl/uvcvideo/)

I've got the exact same problem, except for me Method 1 produced the unchanged high-res image, and Method 2 produces the black image. Any ideas guys?

---

### Post by jack_capvil on 2009-08-03
>                      Originally Posted by **snwbrdr464**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7306338#post7306338")                 
                 this is what worked for me:

first of all if you do not have the program mercurial installed you need that it uses hg to run so that's the program-name you would check:
aptitude install mercurial

then just do these in a terminal and it should work just fine:
hg clone [http://linuxtv.org/hg/~pinchartl/uvcvideo/]("http://linuxtv.org/hg/%7Epinchartl/uvcvideo/")
cd uvcvideo/linux/drivers/media/video/uvc/
patch < ~/path/to/patch_solution1_mirrored.txt
cd ~/uvcvideo/
make
sudo make install
sudo make unload
sudo modprobe uvcvideoI have tried this solution either with the "mirrored" or the "NOTmirrored" patch_solution1 and in every case I obtain the same result, wich mean a functional driver but with the image upside down (a mirrored image).
I noticed when applying the patch an error message concerning the line 371. Could it be possible that in both cases the patch does not work and that by the "make" command I create the "standard" driver?
How could I solve this difficulty?
I use Ubuntu 9.04 (In fact LinuxMint 7 Gloria) and my laptop is a Packard-Bell EasyNote BG48-AU-190FR with a Chicony 1.3M webcam having the following identification : 04f2:b012 Chicony Electronics Co., Ltd 1.3 MPixel UVC webcam
Please any help would be really appreciated!!! Thanks by advance for all your efforts to help me


I have also tried to follow the instructions given by Lantarosa as following :> Should also work for normal ubuntu 9.04, just download the new uvcvideo from here and extract it:

[http://linuxtv.org/hg/~pinchartl/uvcvideo/]("http://linuxtv.org/hg/%7Epinchartl/uvcvideo/")

e.g. tar xjvf uvcvideo.tar.bz2 if you got the bz2 archive.

Save the patch in the folder where you extracted uvcvideo to and change the path in the patch to:

linux/drivers/media/video/uvc/uvc_video.c

Then just execute

patch -p0 < patch_solution1_mirrored.txt 
but I am unable to find inside the patch an information about the path. So I am unable to modify it. Where is located the information that should be modified to work with 9.04 :D

---

### Post by mcurran on 2009-08-03
BUMP!

I too am having the same error when trying to patch:

patch < patch_solution1_mirrored.txt
patching file uvc_video.c
Hunk #1 FAILED at 371.
1 out of 1 hunk FAILED -- saving rejects to file uvc_video.c.rej

I'm using Linux Mint 7 "Gloria" (Kernel:  2.6.28-14-generic amd64)...

Please help.

lsusb:  Bus 001 Device 002: ID 174f:5a35 Syntek 1.3MPixel Web Cam - Asus G1s

---

### Post by gerard.leonardo on 2009-08-07
Hi there,

Same problem here, can't do tha patch thing,

THanks in advance!

---

### Post by Grimarr on 2009-08-09
O, yah. I too have this error at371 line %)

Asus x55sr Ubuntu 9.04 (  2.6.28-14-generic)
04f2:b012 Chicony Electronics Co.

---

### Post by HansdeGoede on 2009-08-10
> **Grimarr said:**
> O, yah. I too have this error at371 line %)

Asus x55sr Ubuntu 9.04 (  2.6.28-14-generic)
04f2:b012 Chicony Electronics Co.

Hi,

I've noticed that you and a few others are still trying to fix this with a kernel patch. As I've explained in a comment in this thread before, that is really not the right way to fix this.

The correct way to fix this is to let libv4l the v4l format conversion library of which I'm the author, do the flipping. Ubuntu has been shipping this library for 2 releases now, and the new 0.6.0 release has a table with DMI identification strings for many Asus laptop models which are known to have an upside down webcam and will correct this automatically without any kernel patching necessary.

If you can send me the necessary information for your laptop I'll happily add that to libv4l for the 0.6.1 release, and I'll send you detailed instructions how to get and install the latest libv4l so that you can fix this quick and easy without needing to patch the kernel.

See this post for what information I need and howto get it:
[http://lists.berlios.de/pipermail/linux-uvc-devel/2009-June/004886.html](http://lists.berlios.de/pipermail/linux-uvc-devel/2009-June/004886.html)

Please send this information in a mail to:
Hans de Goede <jwrdegoede@fedoraproject.org>

Regards,

Hans

p.s.

Please do not copy and paste the dmidecode output, but use the redirection operator '>' as given as example in the mailinglist post and attach the resulting file to the mail. The dmidecode output may contain trailing whitespace which I need and this whitespace may get lost using copy and paste.

---

### Post by Grimarr on 2009-08-10
[quote=HansdeGoede]Please send this information in a mail to:
Hans de Goede <jwrdegoede@fedoraproject.org>
[/quote] sended.
... and nevertheless that with this line &#8470;371.? %))

---

### Post by danitetus on 2009-08-11
Hello, sorry but my english is not very well.

I've tried to follow the steps, but when I run "make uvcvideo" the computer reports this:

> daniel@daniel-poratil:~/trunk$ sudo make uvcvideo
Building USB Video Class driver...
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.28-14-generic'
  CC [M]  /home/daniel/trunk/uvc_driver.o
  CC [M]  /home/daniel/trunk/uvc_queue.o
  CC [M]  /home/daniel/trunk/uvc_v4l2.o
/home/daniel/trunk/uvc_v4l2.c: En la función ‘uvc_v4l2_do_ioctl’:
/home/daniel/trunk/uvc_v4l2.c:986: aviso: se pasa el argumento 1 de ‘v4l_compat_translate_ioctl’ desde un tipo de puntero incompatible
/home/daniel/trunk/uvc_v4l2.c:986: aviso: el paso del argumento 2 de ‘v4l_compat_translate_ioctl’ crea un entero desde un puntero sin una conversión
/home/daniel/trunk/uvc_v4l2.c:986: aviso: el paso del argumento 3 de ‘v4l_compat_translate_ioctl’ crea un puntero desde un entero sin una conversión
/home/daniel/trunk/uvc_v4l2.c:986: error: demasiados argumentos para la función ‘v4l_compat_translate_ioctl’
make[2]: *** [/home/daniel/trunk/uvc_v4l2.o] Error 1
make[1]: *** [_module_/home/daniel/trunk] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.28-14-generic'
make: *** [uvcvideo] Error 2
daniel@daniel-poratil:~/trunk$ Any idea about the problem??? thanks

---

### Post by Grimarr on 2009-08-11
Maybe, you will be helped by reinstallation v4l and accompanying libraries. At least it has helped me with a similar case of %)

---

### Post by mp3guy on 2009-09-18
> **bekirserifoglu said:**
> since uvc_v4l2 has changed in kernel 2.6.28, make gives errors. you need to use file uvc_v4l2.c from kernel source instead of the one from uvc trunk. you can get it from the kernel source. I am attaching a copy of that to make it easier for you. do not forget to change file extension from txt to c. just replace uvc_v4l2.c with the one attached to the post and try to compile again. 

the file size exceeds the forum's limit. so here is the code itself. save it as v4l2.c and put a blank line at the end of the file. 

```
/*
 *      uvc_v4l2.c  --  USB Video Class driver - V4L2 API
 *
 *      Copyright (C) 2005-2008
 *          Laurent Pinchart (laurent.pinchart@skynet.be)
 *
 *      This program is free software; you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation; either version 2 of the License, or
 *      (at your option) any later version.
 *
 */

#include <linux/kernel.h>
#include <linux/version.h>
#include <linux/list.h>
#include <linux/module.h>
#include <linux/usb.h>
#include <linux/videodev2.h>
#include <linux/vmalloc.h>
#include <linux/mm.h>
#include <linux/wait.h>
#include <asm/atomic.h>

#include <media/v4l2-common.h>
#include <media/v4l2-ioctl.h>

#include "uvcvideo.h"

/* ------------------------------------------------------------------------
 * V4L2 interface
 */

/*
 * Mapping V4L2 controls to UVC controls can be straighforward if done well.
 * Most of the UVC controls exist in V4L2, and can be mapped directly. Some
 * must be grouped (for instance the Red Balance, Blue Balance and Do White
 * Balance V4L2 controls use the White Balance Component UVC control) or
 * otherwise translated. The approach we take here is to use a translation
 * table for the controls which can be mapped directly, and handle the others
 * manually.
 */
static int uvc_v4l2_query_menu(struct uvc_video_device *video,
	struct v4l2_querymenu *query_menu)
{
	struct uvc_menu_info *menu_info;
	struct uvc_control_mapping *mapping;
	struct uvc_control *ctrl;

	ctrl = uvc_find_control(video, query_menu->id, &mapping);
	if (ctrl == NULL || mapping->v4l2_type != V4L2_CTRL_TYPE_MENU)
		return -EINVAL;

	if (query_menu->index >= mapping->menu_count)
		return -EINVAL;

	menu_info = &mapping->menu_info[query_menu->index];
	strncpy(query_menu->name, menu_info->name, 32);
	return 0;
}

/*
 * Find the frame interval closest to the requested frame interval for the
 * given frame format and size. This should be done by the device as part of
 * the Video Probe and Commit negotiation, but some hardware don't implement
 * that feature.
 */
static __u32 uvc_try_frame_interval(struct uvc_frame *frame, __u32 interval)
{
	unsigned int i;

	if (frame->bFrameIntervalType) {
		__u32 best = -1, dist;

		for (i = 0; i < frame->bFrameIntervalType; ++i) {
			dist = interval > frame->dwFrameInterval[i]
			     ? interval - frame->dwFrameInterval[i]
			     : frame->dwFrameInterval[i] - interval;

			if (dist > best)
				break;

			best = dist;
		}

		interval = frame->dwFrameInterval[i-1];
	} else {
		const __u32 min = frame->dwFrameInterval[0];
		const __u32 max = frame->dwFrameInterval[1];
		const __u32 step = frame->dwFrameInterval[2];

		interval = min + (interval - min + step/2) / step * step;
		if (interval > max)
			interval = max;
	}

	return interval;
}

static int uvc_v4l2_try_format(struct uvc_video_device *video,
	struct v4l2_format *fmt, struct uvc_streaming_control *probe,
	struct uvc_format **uvc_format, struct uvc_frame **uvc_frame)
{
	struct uvc_format *format = NULL;
	struct uvc_frame *frame = NULL;
	__u16 rw, rh;
	unsigned int d, maxd;
	unsigned int i;
	__u32 interval;
	int ret = 0;
	__u8 *fcc;

	if (fmt->type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
		return -EINVAL;

	fcc = (__u8 *)&fmt->fmt.pix.pixelformat;
	uvc_trace(UVC_TRACE_FORMAT, "Trying format 0x%08x (%c%c%c%c): %ux%u.\n",
			fmt->fmt.pix.pixelformat,
			fcc[0], fcc[1], fcc[2], fcc[3],
			fmt->fmt.pix.width, fmt->fmt.pix.height);

	/* Check if the hardware supports the requested format. */
	for (i = 0; i < video->streaming->nformats; ++i) {
		format = &video->streaming->format[i];
		if (format->fcc == fmt->fmt.pix.pixelformat)
			break;
	}

	if (format == NULL || format->fcc != fmt->fmt.pix.pixelformat) {
		uvc_trace(UVC_TRACE_FORMAT, "Unsupported format 0x%08x.\n",
				fmt->fmt.pix.pixelformat);
		return -EINVAL;
	}

	/* Find the closest image size. The distance between image sizes is
	 * the size in pixels of the non-overlapping regions between the
	 * requested size and the frame-specified size.
	 */
	rw = fmt->fmt.pix.width;
	rh = fmt->fmt.pix.height;
	maxd = (unsigned int)-1;

	for (i = 0; i < format->nframes; ++i) {
		__u16 w = format->frame[i].wWidth;
		__u16 h = format->frame[i].wHeight;

		d = min(w, rw) * min(h, rh);
		d = w*h + rw*rh - 2*d;
		if (d < maxd) {
			maxd = d;
			frame = &format->frame[i];
		}

		if (maxd == 0)
			break;
	}

	if (frame == NULL) {
		uvc_trace(UVC_TRACE_FORMAT, "Unsupported size %ux%u.\n",
				fmt->fmt.pix.width, fmt->fmt.pix.height);
		return -EINVAL;
	}

	/* Use the default frame interval. */
	interval = frame->dwDefaultFrameInterval;
	uvc_trace(UVC_TRACE_FORMAT, "Using default frame interval %u.%u us "
		"(%u.%u fps).\n", interval/10, interval%10, 10000000/interval,
		(100000000/interval)%10);

	/* Set the format index, frame index and frame interval. */
	memset(probe, 0, sizeof *probe);
	probe->bmHint = 1;	/* dwFrameInterval */
	probe->bFormatIndex = format->index;
	probe->bFrameIndex = frame->bFrameIndex;
	probe->dwFrameInterval = uvc_try_frame_interval(frame, interval);
	/* Some webcams stall the probe control set request when the
	 * dwMaxVideoFrameSize field is set to zero. The UVC specification
	 * clearly states that the field is read-only from the host, so this
	 * is a webcam bug. Set dwMaxVideoFrameSize to the value reported by
	 * the webcam to work around the problem.
	 *
	 * The workaround could probably be enabled for all webcams, so the
	 * quirk can be removed if needed. It's currently useful to detect
	 * webcam bugs and fix them before they hit the market (providing
	 * developers test their webcams with the Linux driver as well as with
	 * the Windows driver).
	 */
	if (video->dev->quirks & UVC_QUIRK_PROBE_EXTRAFIELDS)
		probe->dwMaxVideoFrameSize =
			video->streaming->ctrl.dwMaxVideoFrameSize;

	/* Probe the device */
	if ((ret = uvc_probe_video(video, probe)) < 0)
		goto done;

	fmt->fmt.pix.width = frame->wWidth;
	fmt->fmt.pix.height = frame->wHeight;
	fmt->fmt.pix.field = V4L2_FIELD_NONE;
	fmt->fmt.pix.bytesperline = format->bpp * frame->wWidth / 8;
	fmt->fmt.pix.sizeimage = probe->dwMaxVideoFrameSize;
	fmt->fmt.pix.colorspace = format->colorspace;
	fmt->fmt.pix.priv = 0;

	if (uvc_format != NULL)
		*uvc_format = format;
	if (uvc_frame != NULL)
		*uvc_frame = frame;

done:
	return ret;
}

static int uvc_v4l2_get_format(struct uvc_video_device *video,
	struct v4l2_format *fmt)
{
	struct uvc_format *format = video->streaming->cur_format;
	struct uvc_frame *frame = video->streaming->cur_frame;

	if (fmt->type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
		return -EINVAL;

	if (format == NULL || frame == NULL)
		return -EINVAL;

	fmt->fmt.pix.pixelformat = format->fcc;
	fmt->fmt.pix.width = frame->wWidth;
	fmt->fmt.pix.height = frame->wHeight;
	fmt->fmt.pix.field = V4L2_FIELD_NONE;
	fmt->fmt.pix.bytesperline = format->bpp * frame->wWidth / 8;
	fmt->fmt.pix.sizeimage = video->streaming->ctrl.dwMaxVideoFrameSize;
	fmt->fmt.pix.colorspace = format->colorspace;
	fmt->fmt.pix.priv = 0;

	return 0;
}

static int uvc_v4l2_set_format(struct uvc_video_device *video,
	struct v4l2_format *fmt)
{
	struct uvc_streaming_control probe;
	struct uvc_format *format;
	struct uvc_frame *frame;
	int ret;

	if (fmt->type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
		return -EINVAL;

	if (uvc_queue_streaming(&video->queue))
		return -EBUSY;

	ret = uvc_v4l2_try_format(video, fmt, &probe, &format, &frame);
	if (ret < 0)
		return ret;

	memcpy(&video->streaming->ctrl, &probe, sizeof probe);
	video->streaming->cur_format = format;
	video->streaming->cur_frame = frame;

	return 0;
}

static int uvc_v4l2_get_streamparm(struct uvc_video_device *video,
		struct v4l2_streamparm *parm)
{
	uint32_t numerator, denominator;

	if (parm->type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
		return -EINVAL;

	numerator = video->streaming->ctrl.dwFrameInterval;
	denominator = 10000000;
	uvc_simplify_fraction(&numerator, &denominator, 8, 333);

	memset(parm, 0, sizeof *parm);
	parm->type = V4L2_BUF_TYPE_VIDEO_CAPTURE;
	parm->parm.capture.capability = V4L2_CAP_TIMEPERFRAME;
	parm->parm.capture.capturemode = 0;
	parm->parm.capture.timeperframe.numerator = numerator;
	parm->parm.capture.timeperframe.denominator = denominator;
	parm->parm.capture.extendedmode = 0;
	parm->parm.capture.readbuffers = 0;

	return 0;
}

static int uvc_v4l2_set_streamparm(struct uvc_video_device *video,
		struct v4l2_streamparm *parm)
{
	struct uvc_frame *frame = video->streaming->cur_frame;
	struct uvc_streaming_control probe;
	uint32_t interval;
	int ret;

	if (parm->type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
		return -EINVAL;

	if (uvc_queue_streaming(&video->queue))
		return -EBUSY;

	memcpy(&probe, &video->streaming->ctrl, sizeof probe);
	interval = uvc_fraction_to_interval(
			parm->parm.capture.timeperframe.numerator,
			parm->parm.capture.timeperframe.denominator);

	uvc_trace(UVC_TRACE_FORMAT, "Setting frame interval to %u/%u (%u).\n",
			parm->parm.capture.timeperframe.numerator,
			parm->parm.capture.timeperframe.denominator,
			interval);
	probe.dwFrameInterval = uvc_try_frame_interval(frame, interval);

	/* Probe the device with the new settings. */
	if ((ret = uvc_probe_video(video, &probe)) < 0)
		return ret;

	memcpy(&video->streaming->ctrl, &probe, sizeof probe);

	/* Return the actual frame period. */
	parm->parm.capture.timeperframe.numerator = probe.dwFrameInterval;
	parm->parm.capture.timeperframe.denominator = 10000000;
	uvc_simplify_fraction(&parm->parm.capture.timeperframe.numerator,
				&parm->parm.capture.timeperframe.denominator,
				8, 333);

	return 0;
}

/* ------------------------------------------------------------------------
 * Privilege management
 */

/*
 * Privilege management is the multiple-open implementation basis. The current
 * implementation is completely transparent for the end-user and doesn't
 * require explicit use of the VIDIOC_G_PRIORITY and VIDIOC_S_PRIORITY ioctls.
 * Those ioctls enable finer control on the device (by making possible for a
 * user to request exclusive access to a device), but are not mature yet.
 * Switching to the V4L2 priority mechanism might be considered in the future
 * if this situation changes.
 *
 * Each open instance of a UVC device can either be in a privileged or
 * unprivileged state. Only a single instance can be in a privileged state at
 * a given time. Trying to perform an operation which requires privileges will
 * automatically acquire the required privileges if possible, or return -EBUSY
 * otherwise. Privileges are dismissed when closing the instance.
 *
 * Operations which require privileges are:
 *
 * - VIDIOC_S_INPUT
 * - VIDIOC_S_PARM
 * - VIDIOC_S_FMT
 * - VIDIOC_TRY_FMT
 * - VIDIOC_REQBUFS
 */
static int uvc_acquire_privileges(struct uvc_fh *handle)
{
	int ret = 0;

	/* Always succeed if the handle is already privileged. */
	if (handle->state == UVC_HANDLE_ACTIVE)
		return 0;

	/* Check if the device already has a privileged handle. */
	mutex_lock(&uvc_driver.open_mutex);
	if (atomic_inc_return(&handle->device->active) != 1) {
		atomic_dec(&handle->device->active);
		ret = -EBUSY;
		goto done;
	}

	handle->state = UVC_HANDLE_ACTIVE;

done:
	mutex_unlock(&uvc_driver.open_mutex);
	return ret;
}

static void uvc_dismiss_privileges(struct uvc_fh *handle)
{
	if (handle->state == UVC_HANDLE_ACTIVE)
		atomic_dec(&handle->device->active);

	handle->state = UVC_HANDLE_PASSIVE;
}

static int uvc_has_privileges(struct uvc_fh *handle)
{
	return handle->state == UVC_HANDLE_ACTIVE;
}

/* ------------------------------------------------------------------------
 * V4L2 file operations
 */

static int uvc_v4l2_open(struct inode *inode, struct file *file)
{
	struct uvc_video_device *video;
	struct uvc_fh *handle;
	int ret = 0;

	uvc_trace(UVC_TRACE_CALLS, "uvc_v4l2_open\n");
	mutex_lock(&uvc_driver.open_mutex);
	video = video_drvdata(file);

	if (video->dev->state & UVC_DEV_DISCONNECTED) {
		ret = -ENODEV;
		goto done;
	}

	ret = usb_autopm_get_interface(video->dev->intf);
	if (ret < 0)
		goto done;

	/* Create the device handle. */
	handle = kzalloc(sizeof *handle, GFP_KERNEL);
	if (handle == NULL) {
		usb_autopm_put_interface(video->dev->intf);
		ret = -ENOMEM;
		goto done;
	}

	handle->device = video;
	handle->state = UVC_HANDLE_PASSIVE;
	file->private_data = handle;

	kref_get(&video->dev->kref);

done:
	mutex_unlock(&uvc_driver.open_mutex);
	return ret;
}

static int uvc_v4l2_release(struct inode *inode, struct file *file)
{
	struct uvc_video_device *video = video_drvdata(file);
	struct uvc_fh *handle = (struct uvc_fh *)file->private_data;

	uvc_trace(UVC_TRACE_CALLS, "uvc_v4l2_release\n");

	/* Only free resources if this is a privileged handle. */
	if (uvc_has_privileges(handle)) {
		uvc_video_enable(video, 0);

		mutex_lock(&video->queue.mutex);
		if (uvc_free_buffers(&video->queue) < 0)
			uvc_printk(KERN_ERR, "uvc_v4l2_release: Unable to "
					"free buffers.\n");
		mutex_unlock(&video->queue.mutex);
	}

	/* Release the file handle. */
	uvc_dismiss_privileges(handle);
	kfree(handle);
	file->private_data = NULL;

	usb_autopm_put_interface(video->dev->intf);
	kref_put(&video->dev->kref, uvc_delete);
	return 0;
}

static int __uvc_v4l2_do_ioctl(struct file *file,
		     unsigned int cmd, void *arg)
{
	struct video_device *vdev = video_devdata(file);
	struct uvc_video_device *video = video_get_drvdata(vdev);
	struct uvc_fh *handle = (struct uvc_fh *)file->private_data;
	int ret = 0;

	if (uvc_trace_param & UVC_TRACE_IOCTL)
		v4l_printk_ioctl(cmd);

	switch (cmd) {
	/* Query capabilities */
	case VIDIOC_QUERYCAP:
	{
		struct v4l2_capability *cap = arg;

		memset(cap, 0, sizeof *cap);
		strncpy(cap->driver, "uvcvideo", sizeof cap->driver);
		strncpy(cap->card, vdev->name, 32);
		strncpy(cap->bus_info, video->dev->udev->bus->bus_name,
			sizeof cap->bus_info);
		cap->version = DRIVER_VERSION_NUMBER;
		cap->capabilities = V4L2_CAP_VIDEO_CAPTURE
				  | V4L2_CAP_STREAMING;
		break;
	}

	/* Get, Set & Query control */
	case VIDIOC_QUERYCTRL:
		return uvc_query_v4l2_ctrl(video, arg);

	case VIDIOC_G_CTRL:
	{
		struct v4l2_control *ctrl = arg;
		struct v4l2_ext_control xctrl;

		memset(&xctrl, 0, sizeof xctrl);
		xctrl.id = ctrl->id;

		uvc_ctrl_begin(video);
		ret = uvc_ctrl_get(video, &xctrl);
		uvc_ctrl_rollback(video);
		if (ret >= 0)
			ctrl->value = xctrl.value;
		break;
	}

	case VIDIOC_S_CTRL:
	{
		struct v4l2_control *ctrl = arg;
		struct v4l2_ext_control xctrl;

		memset(&xctrl, 0, sizeof xctrl);
		xctrl.id = ctrl->id;
		xctrl.value = ctrl->value;

		uvc_ctrl_begin(video);
		ret = uvc_ctrl_set(video, &xctrl);
		if (ret < 0) {
			uvc_ctrl_rollback(video);
			return ret;
		}
		ret = uvc_ctrl_commit(video);
		break;
	}

	case VIDIOC_QUERYMENU:
		return uvc_v4l2_query_menu(video, arg);

	case VIDIOC_G_EXT_CTRLS:
	{
		struct v4l2_ext_controls *ctrls = arg;
		struct v4l2_ext_control *ctrl = ctrls->controls;
		unsigned int i;

		uvc_ctrl_begin(video);
		for (i = 0; i < ctrls->count; ++ctrl, ++i) {
			ret = uvc_ctrl_get(video, ctrl);
			if (ret < 0) {
				uvc_ctrl_rollback(video);
				ctrls->error_idx = i;
				return ret;
			}
		}
		ctrls->error_idx = 0;
		ret = uvc_ctrl_rollback(video);
		break;
	}

	case VIDIOC_S_EXT_CTRLS:
	case VIDIOC_TRY_EXT_CTRLS:
	{
		struct v4l2_ext_controls *ctrls = arg;
		struct v4l2_ext_control *ctrl = ctrls->controls;
		unsigned int i;

		ret = uvc_ctrl_begin(video);
		if (ret < 0)
			return ret;

		for (i = 0; i < ctrls->count; ++ctrl, ++i) {
			ret = uvc_ctrl_set(video, ctrl);
			if (ret < 0) {
				uvc_ctrl_rollback(video);
				ctrls->error_idx = i;
				return ret;
			}
		}

		ctrls->error_idx = 0;

		if (cmd == VIDIOC_S_EXT_CTRLS)
			ret = uvc_ctrl_commit(video);
		else
			ret = uvc_ctrl_rollback(video);
		break;
	}

	/* Get, Set & Enum input */
	case VIDIOC_ENUMINPUT:
	{
		const struct uvc_entity *selector = video->selector;
		struct v4l2_input *input = arg;
		struct uvc_entity *iterm = NULL;
		u32 index = input->index;
		int pin = 0;

		if (selector == NULL ||
		    (video->dev->quirks & UVC_QUIRK_IGNORE_SELECTOR_UNIT)) {
			if (index != 0)
				return -EINVAL;
			iterm = list_first_entry(&video->iterms,
					struct uvc_entity, chain);
			pin = iterm->id;
		} else if (pin < selector->selector.bNrInPins) {
			pin = selector->selector.baSourceID[index];
			list_for_each_entry(iterm, video->iterms.next, chain) {
				if (iterm->id == pin)
					break;
			}
		}

		if (iterm == NULL || iterm->id != pin)
			return -EINVAL;

		memset(input, 0, sizeof *input);
		input->index = index;
		strncpy(input->name, iterm->name, sizeof input->name);
		if (UVC_ENTITY_TYPE(iterm) == ITT_CAMERA)
			input->type = V4L2_INPUT_TYPE_CAMERA;
		break;
	}

	case VIDIOC_G_INPUT:
	{
		u8 input;

		if (video->selector == NULL ||
		    (video->dev->quirks & UVC_QUIRK_IGNORE_SELECTOR_UNIT)) {
			*(int *)arg = 0;
			break;
		}

		ret = uvc_query_ctrl(video->dev, GET_CUR, video->selector->id,
			video->dev->intfnum, SU_INPUT_SELECT_CONTROL,
			&input, 1);
		if (ret < 0)
			return ret;

		*(int *)arg = input - 1;
		break;
	}

	case VIDIOC_S_INPUT:
	{
		u8 input = *(u32 *)arg + 1;

		if ((ret = uvc_acquire_privileges(handle)) < 0)
			return ret;

		if (video->selector == NULL ||
		    (video->dev->quirks & UVC_QUIRK_IGNORE_SELECTOR_UNIT)) {
			if (input != 1)
				return -EINVAL;
			break;
		}

		if (input > video->selector->selector.bNrInPins)
			return -EINVAL;

		return uvc_query_ctrl(video->dev, SET_CUR, video->selector->id,
			video->dev->intfnum, SU_INPUT_SELECT_CONTROL,
			&input, 1);
	}

	/* Try, Get, Set & Enum format */
	case VIDIOC_ENUM_FMT:
	{
		struct v4l2_fmtdesc *fmt = arg;
		struct uvc_format *format;

		if (fmt->type != V4L2_BUF_TYPE_VIDEO_CAPTURE ||
		    fmt->index >= video->streaming->nformats)
			return -EINVAL;

		format = &video->streaming->format[fmt->index];
		fmt->flags = 0;
		if (format->flags & UVC_FMT_FLAG_COMPRESSED)
			fmt->flags |= V4L2_FMT_FLAG_COMPRESSED;
		strncpy(fmt->description, format->name,
			sizeof fmt->description);
		fmt->description[sizeof fmt->description - 1] = 0;
		fmt->pixelformat = format->fcc;
		break;
	}

	case VIDIOC_TRY_FMT:
	{
		struct uvc_streaming_control probe;

		if ((ret = uvc_acquire_privileges(handle)) < 0)
			return ret;

		return uvc_v4l2_try_format(video, arg, &probe, NULL, NULL);
	}

	case VIDIOC_S_FMT:
		if ((ret = uvc_acquire_privileges(handle)) < 0)
			return ret;

		return uvc_v4l2_set_format(video, arg);

	case VIDIOC_G_FMT:
		return uvc_v4l2_get_format(video, arg);

	/* Frame size enumeration */
	case VIDIOC_ENUM_FRAMESIZES:
	{
		struct v4l2_frmsizeenum *fsize = arg;
		struct uvc_format *format = NULL;
		struct uvc_frame *frame;
		int i;

		/* Look for the given pixel format */
		for (i = 0; i < video->streaming->nformats; i++) {
			if (video->streaming->format[i].fcc ==
					fsize->pixel_format) {
				format = &video->streaming->format[i];
				break;
			}
		}
		if (format == NULL)
			return -EINVAL;

		if (fsize->index >= format->nframes)
			return -EINVAL;

		frame = &format->frame[fsize->index];
		fsize->type = V4L2_FRMSIZE_TYPE_DISCRETE;
		fsize->discrete.width = frame->wWidth;
		fsize->discrete.height = frame->wHeight;
		break;
	}

	/* Frame interval enumeration */
	case VIDIOC_ENUM_FRAMEINTERVALS:
	{
		struct v4l2_frmivalenum *fival = arg;
		struct uvc_format *format = NULL;
		struct uvc_frame *frame = NULL;
		int i;

		/* Look for the given pixel format and frame size */
		for (i = 0; i < video->streaming->nformats; i++) {
			if (video->streaming->format[i].fcc ==
					fival->pixel_format) {
				format = &video->streaming->format[i];
				break;
			}
		}
		if (format == NULL)
			return -EINVAL;

		for (i = 0; i < format->nframes; i++) {
			if (format->frame[i].wWidth == fival->width &&
			    format->frame[i].wHeight == fival->height) {
				frame = &format->frame[i];
				break;
			}
		}
		if (frame == NULL)
			return -EINVAL;

		if (frame->bFrameIntervalType) {
			if (fival->index >= frame->bFrameIntervalType)
				return -EINVAL;

			fival->type = V4L2_FRMIVAL_TYPE_DISCRETE;
			fival->discrete.numerator =
				frame->dwFrameInterval[fival->index];
			fival->discrete.denominator = 10000000;
			uvc_simplify_fraction(&fival->discrete.numerator,
				&fival->discrete.denominator, 8, 333);
		} else {
			fival->type = V4L2_FRMIVAL_TYPE_STEPWISE;
			fival->stepwise.min.numerator =
				frame->dwFrameInterval[0];
			fival->stepwise.min.denominator = 10000000;
			fival->stepwise.max.numerator =
				frame->dwFrameInterval[1];
			fival->stepwise.max.denominator = 10000000;
			fival->stepwise.step.numerator =
				frame->dwFrameInterval[2];
			fival->stepwise.step.denominator = 10000000;
			uvc_simplify_fraction(&fival->stepwise.min.numerator,
				&fival->stepwise.min.denominator, 8, 333);
			uvc_simplify_fraction(&fival->stepwise.max.numerator,
				&fival->stepwise.max.denominator, 8, 333);
			uvc_simplify_fraction(&fival->stepwise.step.numerator,
				&fival->stepwise.step.denominator, 8, 333);
		}
		break;
	}

	/* Get & Set streaming parameters */
	case VIDIOC_G_PARM:
		return uvc_v4l2_get_streamparm(video, arg);

	case VIDIOC_S_PARM:
		if ((ret = uvc_acquire_privileges(handle)) < 0)
			return ret;

		return uvc_v4l2_set_streamparm(video, arg);

	/* Cropping and scaling */
	case VIDIOC_CROPCAP:
	{
		struct v4l2_cropcap *ccap = arg;
		struct uvc_frame *frame = video->streaming->cur_frame;

		if (ccap->type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
			return -EINVAL;

		ccap->bounds.left = 0;
		ccap->bounds.top = 0;
		ccap->bounds.width = frame->wWidth;
		ccap->bounds.height = frame->wHeight;

		ccap->defrect = ccap->bounds;

		ccap->pixelaspect.numerator = 1;
		ccap->pixelaspect.denominator = 1;
		break;
	}

	case VIDIOC_G_CROP:
	case VIDIOC_S_CROP:
		return -EINVAL;

	/* Buffers & streaming */
	case VIDIOC_REQBUFS:
	{
		struct v4l2_requestbuffers *rb = arg;
		unsigned int bufsize =
			video->streaming->ctrl.dwMaxVideoFrameSize;

		if (rb->type != V4L2_BUF_TYPE_VIDEO_CAPTURE ||
		    rb->memory != V4L2_MEMORY_MMAP)
			return -EINVAL;

		if ((ret = uvc_acquire_privileges(handle)) < 0)
			return ret;

		ret = uvc_alloc_buffers(&video->queue, rb->count, bufsize);
		if (ret < 0)
			return ret;

		rb->count = ret;
		ret = 0;
		break;
	}

	case VIDIOC_QUERYBUF:
	{
		struct v4l2_buffer *buf = arg;

		if (buf->type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
			return -EINVAL;

		if (!uvc_has_privileges(handle))
			return -EBUSY;

		return uvc_query_buffer(&video->queue, buf);
	}

	case VIDIOC_QBUF:
		if (!uvc_has_privileges(handle))
			return -EBUSY;

		return uvc_queue_buffer(&video->queue, arg);

	case VIDIOC_DQBUF:
		if (!uvc_has_privileges(handle))
			return -EBUSY;

		return uvc_dequeue_buffer(&video->queue, arg,
			file->f_flags & O_NONBLOCK);

	case VIDIOC_STREAMON:
	{
		int *type = arg;

		if (*type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
			return -EINVAL;

		if (!uvc_has_privileges(handle))
			return -EBUSY;

		if ((ret = uvc_video_enable(video, 1)) < 0)
			return ret;
		break;
	}

	case VIDIOC_STREAMOFF:
	{
		int *type = arg;

		if (*type != V4L2_BUF_TYPE_VIDEO_CAPTURE)
			return -EINVAL;

		if (!uvc_has_privileges(handle))
			return -EBUSY;

		return uvc_video_enable(video, 0);
	}

	/* Analog video standards make no sense for digital cameras. */
	case VIDIOC_ENUMSTD:
	case VIDIOC_QUERYSTD:
	case VIDIOC_G_STD:
	case VIDIOC_S_STD:

	case VIDIOC_OVERLAY:

	case VIDIOC_ENUMAUDIO:
	case VIDIOC_ENUMAUDOUT:

	case VIDIOC_ENUMOUTPUT:
		uvc_trace(UVC_TRACE_IOCTL, "Unsupported ioctl 0x%08x\n", cmd);
		return -EINVAL;

	/* Dynamic controls. */
	case UVCIOC_CTRL_ADD:
	{
		struct uvc_xu_control_info *xinfo = arg;
		struct uvc_control_info *info;

		if (!capable(CAP_SYS_ADMIN))
			return -EPERM;

		info = kmalloc(sizeof *info, GFP_KERNEL);
		if (info == NULL)
			return -ENOMEM;

		memcpy(info->entity, xinfo->entity, sizeof info->entity);
		info->index = xinfo->index;
		info->selector = xinfo->selector;
		info->size = xinfo->size;
		info->flags = xinfo->flags;

		info->flags |= UVC_CONTROL_GET_MIN | UVC_CONTROL_GET_MAX |
				UVC_CONTROL_GET_RES | UVC_CONTROL_GET_DEF;

		ret = uvc_ctrl_add_info(info);
		if (ret < 0)
			kfree(info);
		break;
	}

	case UVCIOC_CTRL_MAP:
	{
		struct uvc_xu_control_mapping *xmap = arg;
		struct uvc_control_mapping *map;

		if (!capable(CAP_SYS_ADMIN))
			return -EPERM;

		map = kmalloc(sizeof *map, GFP_KERNEL);
		if (map == NULL)
			return -ENOMEM;

		map->id = xmap->id;
		memcpy(map->name, xmap->name, sizeof map->name);
		memcpy(map->entity, xmap->entity, sizeof map->entity);
		map->selector = xmap->selector;
		map->size = xmap->size;
		map->offset = xmap->offset;
		map->v4l2_type = xmap->v4l2_type;
		map->data_type = xmap->data_type;

		ret = uvc_ctrl_add_mapping(map);
		if (ret < 0)
			kfree(map);
		break;
	}

	case UVCIOC_CTRL_GET:
		return uvc_xu_ctrl_query(video, arg, 0);

	case UVCIOC_CTRL_SET:
		return uvc_xu_ctrl_query(video, arg, 1);

	default:
		if ((ret = v4l_compat_translate_ioctl(file, cmd, arg,
			__uvc_v4l2_do_ioctl)) == -ENOIOCTLCMD)
			uvc_trace(UVC_TRACE_IOCTL, "Unknown ioctl 0x%08x\n",
				  cmd);
		return ret;
	}

	return ret;
}

static int uvc_v4l2_do_ioctl(struct inode *inode, struct file *file,
			      unsigned int cmd, void *arg)
{
	return __uvc_v4l2_do_ioctl(file, cmd, arg);
}

static int uvc_v4l2_ioctl(struct inode *inode, struct file *file,
		     unsigned int cmd, unsigned long arg)
{
	uvc_trace(UVC_TRACE_CALLS, "uvc_v4l2_ioctl\n");
	return video_usercopy(inode, file, cmd, arg, uvc_v4l2_do_ioctl);
}

static ssize_t uvc_v4l2_read(struct file *file, char __user *data,
		    size_t count, loff_t *ppos)
{
	uvc_trace(UVC_TRACE_CALLS, "uvc_v4l2_read: not implemented.\n");
	return -ENODEV;
}

/*
 * VMA operations.
 */
static void uvc_vm_open(struct vm_area_struct *vma)
{
	struct uvc_buffer *buffer = vma->vm_private_data;
	buffer->vma_use_count++;
}

static void uvc_vm_close(struct vm_area_struct *vma)
{
	struct uvc_buffer *buffer = vma->vm_private_data;
	buffer->vma_use_count--;
}

static struct vm_operations_struct uvc_vm_ops = {
	.open		= uvc_vm_open,
	.close		= uvc_vm_close,
};

static int uvc_v4l2_mmap(struct file *file, struct vm_area_struct *vma)
{
	struct uvc_video_device *video = video_drvdata(file);
	struct uvc_buffer *uninitialized_var(buffer);
	struct page *page;
	unsigned long addr, start, size;
	unsigned int i;
	int ret = 0;

	uvc_trace(UVC_TRACE_CALLS, "uvc_v4l2_mmap\n");

	start = vma->vm_start;
	size = vma->vm_end - vma->vm_start;

	mutex_lock(&video->queue.mutex);

	for (i = 0; i < video->queue.count; ++i) {
		buffer = &video->queue.buffer[i];
		if ((buffer->buf.m.offset >> PAGE_SHIFT) == vma->vm_pgoff)
			break;
	}

	if (i == video->queue.count || size != video->queue.buf_size) {
		ret = -EINVAL;
		goto done;
	}

	/*
	 * VM_IO marks the area as being an mmaped region for I/O to a
	 * device. It also prevents the region from being core dumped.
	 */
	vma->vm_flags |= VM_IO;

	addr = (unsigned long)video->queue.mem + buffer->buf.m.offset;
	while (size > 0) {
		page = vmalloc_to_page((void *)addr);
		if ((ret = vm_insert_page(vma, start, page)) < 0)
			goto done;

		start += PAGE_SIZE;
		addr += PAGE_SIZE;
		size -= PAGE_SIZE;
	}

	vma->vm_ops = &uvc_vm_ops;
	vma->vm_private_data = buffer;
	uvc_vm_open(vma);

done:
	mutex_unlock(&video->queue.mutex);
	return ret;
}

static unsigned int uvc_v4l2_poll(struct file *file, poll_table *wait)
{
	struct uvc_video_device *video = video_drvdata(file);

	uvc_trace(UVC_TRACE_CALLS, "uvc_v4l2_poll\n");

	return uvc_queue_poll(&video->queue, file, wait);
}

struct file_operations uvc_fops = {
	.owner		= THIS_MODULE,
	.open		= uvc_v4l2_open,
	.release	= uvc_v4l2_release,
	.ioctl		= uvc_v4l2_ioctl,
	.compat_ioctl	= v4l_compat_ioctl32,
	.llseek		= no_llseek,
	.read		= uvc_v4l2_read,
	.mmap		= uvc_v4l2_mmap,
	.poll		= uvc_v4l2_poll,
};


```

This worked for me. Instead of 

```

sudo modprobe -f uvcvideo

```

I used:

```

sudo modprobe uvcvideo

```

at the end.

---

### Post by nightfrost on 2009-09-19
I haven't followed this thread for a while now, so pardon me if I'm repeating something that's already been said.

In Karmic, this patch is no longer needed, as libv4l 0.6.0 adds support for flipping images on broken laptops. More here: [http://lwn.net/Articles/341030/](http://lwn.net/Articles/341030/)

---

### Post by HansdeGoede on 2009-09-19
> **nightfrost said:**
> I haven't followed this thread for a while now, so pardon me if I'm repeating something that's already been said.

In Karmic, this patch is no longer needed, as libv4l 0.6.0 adds support for flipping images on broken laptops. More here: [http://lwn.net/Articles/341030/](http://lwn.net/Articles/341030/)

Note that libv4l-0.6.1 is already out, and has a much longer known to
be upside down list. Also there are even more upside down models listed
in my mercurial tree:
[http://linuxtv.org/hg/~hgoede/libv4l](http://linuxtv.org/hg/~hgoede/libv4l)

---

### Post by hifi25nl on 2009-09-19
HansdeGoede, please add this camera:

Sony vaio FZ18E. Bus 003 Device 002: ID 05ca:1837 Ricoh Co., Ltd. Image is upside down in all applications.

See also:

[http://bitbucket.org/ahixon/r5u87x/issue/7/image-upside-down-on-05ca-1837](http://bitbucket.org/ahixon/r5u87x/issue/7/image-upside-down-on-05ca-1837)

---

### Post by HansdeGoede on 2009-09-21
> **hifi25nl said:**
> HansdeGoede, please add this camera:

Sony vaio FZ18E. Bus 003 Device 002: ID 05ca:1837 Ricoh Co., Ltd. Image is upside down in all applications.

See also:

[http://bitbucket.org/ahixon/r5u87x/issue/7/image-upside-down-on-05ca-1837](http://bitbucket.org/ahixon/r5u87x/issue/7/image-upside-down-on-05ca-1837)

This camera can do the flipping in hardware, here is a patch to the firmware loader which enables this, and fixed the upside down issue, you will need to recompile the loader with this:
[http://people.atrpms.net/~hdegoede/r5u87x-loader-flip.patch](http://people.atrpms.net/~hdegoede/r5u87x-loader-flip.patch)

Regards,

Hans

---

### Post by efernandespt on 2009-09-26
I have made the lib from [http://linuxtv.org/hg/~hgoede/libv4l/file/0cd02d37173c](http://linuxtv.org/hg/~hgoede/libv4l/file/0cd02d37173c). The upside down is solve but now it's mirrored (has two images)...

---

### Post by arjos85 on 2009-09-27
> **efernandespt said:**
> I have made the lib from [http://linuxtv.org/hg/~hgoede/libv4l/file/0cd02d37173c]("http://linuxtv.org/hg/%7Ehgoede/libv4l/file/0cd02d37173c"). The upside down is solve but now it's mirrored (has two images)...

Tell us something more about what you have done, how people can use it and which problem you got 
thank you ;)

---

### Post by HansdeGoede on 2009-09-27
> **efernandespt said:**
> I have made the lib from [http://linuxtv.org/hg/~hgoede/libv4l/file/0cd02d37173c](http://linuxtv.org/hg/~hgoede/libv4l/file/0cd02d37173c). The upside down is solve but now it's mirrored (has two images)...

Thats rather weird. Which application are you using to view the webcam images ? And what is the usb-id of your webcam ? (See "lsusb" command output, if you don't know which line is your webcam just copy and paste
the whole output here).

Thanks,

Hans

---

### Post by d.tamm on 2009-10-02
> **HansdeGoede said:**
> This camera can do the flipping in hardware, here is a patch to the firmware loader which enables this, and fixed the upside down issue, you will need to recompile the loader with this:
[http://people.atrpms.net/~hdegoede/r5u87x-loader-flip.patch](http://people.atrpms.net/~hdegoede/r5u87x-loader-flip.patch)

Regards,

Hans

people.atrpms.net seems to be down. Is there any other place where I can get the patch? Google did not give any other address.

---

### Post by HansdeGoede on 2009-10-02
> **d.tamm said:**
> people.atrpms.net seems to be down. Is there any other place where I can get the patch? Google did not give any other address.

Ah, yes, sorry about that (not my site just a user). Here is the same
patch on a different url:
[http://people.fedoraproject.org/~jwrdegoede/r5u87x-loader-flip.patch](http://people.fedoraproject.org/~jwrdegoede/r5u87x-loader-flip.patch)

---

### Post by hifi25nl on 2009-10-06
The patch r5u87x-loader-flip.patch is giving me an error message

> patching file loader.c
Hunk #1 FAILED at 35.
1 out of 11 hunks FAILED

Where can I get the right version of the loader?

---

### Post by HansdeGoede on 2009-10-06
> **hifi25nl said:**
> The patch r5u87x-loader-flip.patch is giving me an error message



Where can I get the right version of the loader?

[http://bitbucket.org/ahixon/r5u87x/get/32a27008b8b9.bz2](http://bitbucket.org/ahixon/r5u87x/get/32a27008b8b9.bz2)

Which is a .tar.bz2 file

Regards,

Hans

---

### Post by hifi25nl on 2009-10-08
Sorry but the problem persists. 
I have checked the patch and the file is not the right one!

---

### Post by HansdeGoede on 2009-10-09
> **hifi25nl said:**
> Sorry but the problem persists. 
I have checked the patch and the file is not the right one!

Sorry,

You are completely right, the patch I've provided should be applied on top
of this one:
[http://people.fedoraproject.org/~jwrdegoede/r5u87x-loader-firmware_path.patch](http://people.fedoraproject.org/~jwrdegoede/r5u87x-loader-firmware_path.patch)

Whicc moves the firmware files to the standard /lib/firmware directory.

So download:
[http://bitbucket.org/ahixon/r5u87x/get/32a27008b8b9.bz2](http://bitbucket.org/ahixon/r5u87x/get/32a27008b8b9.bz2)

And then apply:
[http://people.fedoraproject.org/~jwrdegoede/r5u87x-loader-firmware_path.patch](http://people.fedoraproject.org/~jwrdegoede/r5u87x-loader-firmware_path.patch)

Followed by:
[http://people.fedoraproject.org/~jwrdegoede/r5u87x-loader-flip.patch](http://people.fedoraproject.org/~jwrdegoede/r5u87x-loader-flip.patch)

And then do the usual ./configure, make, make install

Also if your distro (Ubuntu I guess) provides packages of the loader, please consider filing a bug with a link to the flip patch and ask them to
include this.

Sorry for not providing proper instructions before,

Regards,

Hans

---

### Post by jf-otto on 2009-10-13
Hi, thanks to all for all the info in the thread.

I´ve tryied many options till I reed about the update of libv4l. I'm trying that now, but I don't know what to do after compile :confused: I reed the info in the text files in the root of the lib source but didn't find any there... I suppose maybe that's to basic to include there, but I had no lucky searching for "install libv4l"... BTW, I dowloaded this file: libv4l-33606f40c9ca.tar.bz2

The compiling seems to be ok, just a few warnings here and there, but I'm sttuck...

Hans, I didn't send you the info becouse I don't know if it's already in the table (becouse I could not prove it) I'll copy it here, if it's better for you have it in your mail just say it and I'll send it.

[PHP]Vendor
ASUSTeK Computer Inc.        

Name
K50IJ    

Usblog
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0603:b5d3 Novatek Microelectronics Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/PHP]

Any help is welcome!

Thanks!

---

### Post by HansdeGoede on 2009-10-13
> **jf-otto said:**
> Hi, thanks to all for all the info in the thread.

I´ve tryied many options till I reed about the update of libv4l. I'm trying that now, but I don't know what to do after compile :confused: I reed the info in the text files in the root of the lib source but didn't find any there... I suppose maybe that's to basic to include there, but I had no lucky searching for "install libv4l"... BTW, I dowloaded this file: libv4l-33606f40c9ca.tar.bz2

The compiling seems to be ok, just a few warnings here and there, but I'm sttuck...

Hans, I didn't send you the info becouse I don't know if it's already in the table (becouse I could not prove it) I'll copy it here, if it's better for you have it in your mail just say it and I'll send it.

[PHP]Vendor
ASUSTeK Computer Inc.        

Name
K50IJ    

Usblog
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0603:b5d3 Novatek Microelectronics Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/PHP]

Any help is welcome!

Thanks!

Ok,

So for those who wish to try and see if libv4l fixes their upside down
issue (it has a list of 40 + laptop models included now, so should work
out of the box on most machines), do the following:

Download:
[http://people.fedoraproject.org/~jwrdegoede/libv4l-0.6.3-test.tar.gz](http://people.fedoraproject.org/~jwrdegoede/libv4l-0.6.3-test.tar.gz)

Then to make sure no old versions get in the way (only needed if you've
tried to install libv4l manually before):
rm -fr /usr/lib*/libv4l* /usr/local/lib*/libv4l*

And then follow these instructions to install the new version:
[http://hansdegoede.livejournal.com/7622.html](http://hansdegoede.livejournal.com/7622.html)

Regards,

Hans

---

### Post by jf-otto on 2009-10-13
Thanks a lot! I've just tested it with cheese and it works perfect. Tell me if some other info is usefull for you, I would be pleased to be of some help!

Best regards

---

### Post by cj4linux on 2009-10-16
Hans, that's great, thanks much!  For anyone else, I'm using an Asus G50VT-X5.  Spent alot of time fishing around--it's such a common problem, that's there's a lot different approaches.  For me, this approach worked well.  I use the *0.6.2 version and followed your directions you noted on [http://hansdegoede.livejournal.com/7622.html](http://hansdegoede.livejournal.com/7622.html).

Thanks again!

---

### Post by cj4linux on 2009-10-17
Sorry, I spoke too soon...the image has been corrected in Cheese, but is still upside down in skype which will be all of my use.  The skype version is 2.1.0.47.  Any ideas?

---

### Post by cj4linux on 2009-10-17
I'm getting this when I'm trying to use LD_PRELOAD with skype:
ERROR: ld.so: object '/usr/lib64/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

I'm using the 64-bit beta version of skype, version number noted above.

---

### Post by cj4linux on 2009-10-17
Okay, got it, sorry for the multiple posts, but if it helps someone else, then great.

Anyway, I'm running beta 9.10, 64-bit, on the aforementioned Asus laptop above.  I followed Hans instructions.  I installed the 64-bit beta skype for 8.10 on their download page.  When passing the LD_PRELOAD, I used the 32bit one LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype which works perfectly.  Then, to beautify, I created a launching script & edit the menu launcher to call that script when I select skype from Applications-->Internet-->Skype.  So, stepwise:
1.)  Follow Hans instructions in this thread
2.)  Install the skype client
3.)  Invoke skype with LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype (either on the command line, or edit a launcher.)

Thanks again Hans, for the work.  I've tried some of the other approaches, vfile, driver mods, etc; but, this got me what I wanted--a functioning web cam w/skype & cheese, etc.

---

### Post by HansdeGoede on 2009-10-17
> **cj4linux said:**
> I'm getting this when I'm trying to use LD_PRELOAD with skype:
ERROR: ld.so: object '/usr/lib64/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

I'm using the 64-bit beta version of skype, version number noted above.

I think the 64 bit beta might in reality still be 32 bit (I think I've had the same bug report before and that was the cause) try pre-loading the
32 bit v4l1compat.so.

Regards,

Hans

---

### Post by cj4linux on 2009-10-17
Thanks Hans, I gave that a go, and everything's working splendly now :)

---

### Post by vascot on 2009-10-20
Yes, my webcam in my ASUS f3ke is fliped the right way:)  Thanks to Hans: [http://hansdegoede.livejournal.com/7622.html](http://hansdegoede.livejournal.com/7622.html)

---

### Post by jigoita on 2009-10-21
> **HansdeGoede said:**
> Sorry,

You are completely right, the patch I've provided should be applied on top
of this one:
[http://people.fedoraproject.org/~jwrdegoede/r5u87x-loader-firmware_path.patch]("http://people.fedoraproject.org/%7Ejwrdegoede/r5u87x-loader-firmware_path.patch")

Whicc moves the firmware files to the standard /lib/firmware directory.

So download:
[http://bitbucket.org/ahixon/r5u87x/get/32a27008b8b9.bz2](http://bitbucket.org/ahixon/r5u87x/get/32a27008b8b9.bz2)

And then apply:
[http://people.fedoraproject.org/~jwrdegoede/r5u87x-loader-firmware_path.patch]("http://people.fedoraproject.org/%7Ejwrdegoede/r5u87x-loader-firmware_path.patch")

Followed by:
[http://people.fedoraproject.org/~jwrdegoede/r5u87x-loader-flip.patch]("http://people.fedoraproject.org/%7Ejwrdegoede/r5u87x-loader-flip.patch")

And then do the usual ./configure, make, make install

Also if your distro (Ubuntu I guess) provides packages of the loader, please consider filing a bug with a link to the flip patch and ask them to
include this.

Sorry for not providing proper instructions before,

Regards,

Hans

Great! Thanks!! I spent several hours researching on internet, and only your solution was successful for me! Here a VAIO VGN-FZ18M. Now the webcam is not "upside down" anymore, and we can use Skype perfectly.

Thousand thanks!!!!!!! :P

---

### Post by kiloxxx on 2009-10-22
> **jigoita said:**
> Great! Thanks!! I spent several hours researching on internet, and only your solution was successful for me! Here a VAIO VGN-FZ18M. Now the webcam is not "upside down" anymore, and we can use Skype perfectly.

Thousand thanks!!!!!!! :P


The solution provided by HansdeGoede works for me too, on a Vaio VGN-FZ11Z. Also the second patch at the beginning of this post had worked, but I had problems with the vloopback module for Webcamstudio. Now everything is working.
Thank a lot!

---

### Post by boom2k1 on 2009-11-01
I can confirm [http://hansdegoede.livejournal.com/7622.html](http://hansdegoede.livejournal.com/7622.html)
's solution
   - libv4l  [http://apps.freshmeat.net/projects/libv4l](http://apps.freshmeat.net/projects/libv4l)
   - his installation instruction + installing another package he mentioned there
 works for my Ubuntu 9.10 with Skype installed from the medibuntu repository on the default webcam of my new Asus UL30A laptop.
I am glad the upside down problem is finally fixed!

---

### Post by Renseih on 2009-11-02
Hi, none of the solutions provided here has helped me to fix the upside-down-problem.

I am running Ubuntu 9.10 64bit on an Asus Notebook (X53Ka AP051-C).

> lsusb outputs:

```
Bus 001 Device 004: ID 174f:5a35 Syntek Sonix 1.3MPixel USB 2.0 Camera
```When I try one of the patches provided by arjos85 and compile the new file, I get a warning:

> guido@Sydney:~/trunk$ make
-------------------------------- WARNING ---------------------------------------
 The USB Video Class driver has moved to [http://linuxtv.org/](http://linuxtv.org/).
 Using the Berlios SVN repository is now deprecated.
 Please check [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) for download instructions.
 If you really want to compile this historical version, run 'make uvcvideo'.
--------------------------------------------------------------------------------
Entering 
> guido@Sydney:~/trunk$ make uvcvideooutputs several error messages.

So I tried the solution provided by HansdeGoede here:
[http://hansdegoede.livejournal.com/7622.html](http://hansdegoede.livejournal.com/7622.html)

But neither
> LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so skype
 nor > LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
  nor 

 > LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real work. Skype starts but the webcam-pic is still upside-down. Cheese does not work correctly, too.
 

 I googled up and down and up but could not find any other solution....Is there really no way to get this damned webcam working?????

---

### Post by HansdeGoede on 2009-11-03
> **Renseih said:**
> Hi, none of the solutions provided here has helped me to fix the upside-down-problem.

So I tried the solution provided by HansdeGoede here:
[http://hansdegoede.livejournal.com/7622.html](http://hansdegoede.livejournal.com/7622.html)


This means that libv4l does not yet know about your laptop, please
do (as root):
dmidecode > dmi.log
lsusb > usb.log

And send a mail with the 2 files attached to: [email]hdegoede@redhat.com[/email] 

Do not copy and paste the files, do not modify them! I need them
100% as is, so please attach them as is.

---

### Post by Renseih on 2009-11-06
Thank you soooooooooooooooooooooooooooooooooo much Hans!  Finally my webcam works correctly!!!!!!!!!!!!!!!!!!!!!!!! Cant believe  it. 

I tried it so many times to fix this webcam alone, but it never  worked...I almost got crazy and was already thinking about ripping off  the Notebook to turn the camera around - and now it works.... Juhu!!!!!!

Guido

---

### Post by fckivanc on 2009-11-06
thanks HansdeGoede
libv4l 0.6.3 worked for my asus u6v but the image is mirrored.

---

### Post by sireon on 2009-11-07
Hi there!

I have the same problem that Renseih had (post #178).
Running Ubuntu 9.10 32bit on Asus k50 ab, my built in chicony cam refuses to produce correct video, just that upside-down one. I have spent my time on crawling for a solution, finally I did everything as Renseih did, still no result. 

Could you please help me with something? I attach my dmi&usb logs. Thanks in advance!

---

### Post by CANN1 on 2009-11-10
pls help me

-----------------------------------------------------------

worldlan@worldlan:~$ cd trunk
worldlan@worldlan:~/trunk$ make
-------------------------------- WARNING ---------------------------------------
 The USB Video Class driver has moved to [http://linuxtv.org/](http://linuxtv.org/).
 Using the Berlios SVN repository is now deprecated.
 Please check [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) for download instructions.
 If you really want to compile this historical version, run 'make uvcvideo'.
--------------------------------------------------------------------------------
worldlan@worldlan:~/trunk$ make uvcvideo
Building USB Video Class driver...
make[1]:`/usr/src/linux-headers-2.6.31-14-generic' dizinine giriliyor
  CC [M]  /home/worldlan/trunk/uvc_driver.o
/home/worldlan/trunk/uvc_driver.c: In function ‘uvc_register_video’:
/home/worldlan/trunk/uvc_driver.c:1491: warning: assignment from incompatible pointer type
  CC [M]  /home/worldlan/trunk/uvc_v4l2.o
/home/worldlan/trunk/uvc_v4l2.c: In function ‘uvc_v4l2_do_ioctl’:
/home/worldlan/trunk/uvc_v4l2.c:986: warning: passing argument 1 of ‘v4l_compat_translate_ioctl’ from incompatible pointer type
include/media/v4l2-ioctl.h:285: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/worldlan/trunk/uvc_v4l2.c:986: warning: passing argument 2 of ‘v4l_compat_translate_ioctl’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:285: note: expected ‘int’ but argument is of type ‘struct file *’
/home/worldlan/trunk/uvc_v4l2.c:986: warning: passing argument 3 of ‘v4l_compat_translate_ioctl’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:285: note: expected ‘void *’ but argument is of type ‘unsigned int’
/home/worldlan/trunk/uvc_v4l2.c:986: error: too many arguments to function ‘v4l_compat_translate_ioctl’
/home/worldlan/trunk/uvc_v4l2.c: In function ‘uvc_v4l2_ioctl’:
/home/worldlan/trunk/uvc_v4l2.c:999: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/worldlan/trunk/uvc_v4l2.c:999: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/worldlan/trunk/uvc_v4l2.c:999: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘long unsigned int’
/home/worldlan/trunk/uvc_v4l2.c:999: error: too many arguments to function ‘video_usercopy’
/home/worldlan/trunk/uvc_v4l2.c: At top level:
/home/worldlan/trunk/uvc_v4l2.c:1097: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
make[2]: *** [/home/worldlan/trunk/uvc_v4l2.o] Hata 1
make[1]: *** [_module_/home/worldlan/trunk] Hata 2
make[1]: `/usr/src/linux-headers-2.6.31-14-generic' dizininden ç&#305;k&#305;l&#305;yor
make: *** [uvcvideo] Hata 2
worldlan@worldlan:~/trunk$ INSTALL_MOD_DIR := usb/media
INSTALL_MOD_DIR: command not found
worldlan@worldlan:~/trunk$ ^C
worldlan@worldlan:~/trunk$

---

### Post by charlesopondo on 2009-11-12
I found a 3-step solution here that does not involve kernel patching, that worked for my Asus B50A, Ubuntu 9.10, KDE: [http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/#comment-896]("http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/#comment-896")

---

### Post by HansdeGoede on 2009-11-13
> **fckivanc said:**
> thanks HansdeGoede
libv4l 0.6.3 worked for my asus u6v but the image is mirrored.

Hmm, are you sure, try writing "hello" on a piece of paper, and then hold it up in front of the camera, you should be able to read it normally.

Many people expect a camera to work as a mirror, but it is not supposed too, so unlike with a mirror the text should be readable.

---

### Post by HansdeGoede on 2009-11-13
> **sireon said:**
> Hi there!

I have the same problem that Renseih had (post #178).
Running Ubuntu 9.10 32bit on Asus k50 ab, my built in chicony cam refuses to produce correct video, just that upside-down one. I have spent my time on crawling for a solution, finally I did everything as Renseih did, still no result. 

Could you please help me with something? I attach my dmi&usb logs. Thanks in advance!

Hi,

Your laptop info is included in the latest libv4l, which can be downloaded here:
[http://people.fedoraproject.org/~jwrdegoede/libv4l-0.6.4-test.tar.gz](http://people.fedoraproject.org/~jwrdegoede/libv4l-0.6.4-test.tar.gz)

Install instructions are here:
[http://hansdegoede.livejournal.com/7622.html](http://hansdegoede.livejournal.com/7622.html)

Regards,

Hans

---

### Post by Romanrp on 2009-11-15
Is there any way to reverse this since now my webcam doesn't work at all.

---

### Post by sireon on 2009-11-16
Thank you Hans!
I will try it and report.

---

### Post by lepadatu.lucian on 2009-11-21
Thank you Hans.I tried many patches that didn't work till I found your library. It works just fine on my Asus F7Sseries (Chicony 1.3 mega pixels camera). I like the open source OS and linux community. Good job!

---

### Post by fckivanc on 2009-11-29
> **HansdeGoede said:**
> Hmm, are you sure, try writing "hello" on a piece of paper, and then hold it up in front of the camera, you should be able to read it normally.

Many people expect a camera to work as a mirror, but it is not supposed too, so unlike with a mirror the text should be readable.

The weird thing is the image is mirrored with skype but not with cheese (all effects are off).

---

### Post by HansdeGoede on 2009-11-29
Hi,

> **fckivanc said:**
> The weird thing is the image is mirrored with skype but not with cheese (all effects are off).

Ah, that issue, yes I've been getting more reports about that recently. This is some weird issue with skype, which seems to be introduced by a recent skype version (or people just started noticing it).

What you can do is install v4l2ucp, and with that check the hflip option
(that libv4l adds to your cam) when using skype. It would be good to
first check how the receiving end sees you, maybe skype only does the mirroring in the local display.

Regards,

Hans

---

### Post by fckivanc on 2009-12-05
Yes this is an issue with the recent version of skype (2.1.0.47). I installed version 2.0.0.72 today. Problem solved.

---

### Post by someNewb on 2009-12-19
while the driver in first post compiles it gave a lot of errors and didn't compile at all

however, i tried hans's solution but after redownloading the libv4l from [here]("https://launchpad.net/%7Elibv4l/+archive/ppa") it didn't fix my flipped camera

i guess my camera isn't on the flipped cameras list yet :(

---

### Post by svtfmook on 2009-12-19
ok, i followed this, now my webcam doesn't work at all.  how would i go about reinstalling my original driver?

9.10, 64bit, chicony cnf7129 integrated webcam on an asus k70 laptop

---

### Post by someNewb on 2009-12-20
[B]Awesome! 
[/B]i contacted hans with the 2 files for which he asked and he added my webcam into the list of flipped camera devices. 
NOW IT WORKS! 
([explanation that someone posted before is here]("http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/comment-page-3/"))

thanks hans!

---

### Post by mikewhatever on 2009-12-20
> **someNewb said:**
> [B]Awesome! 
[/B]i contacted hans with the 2 files for which he asked and he added my webcam into the list of flipped camera devices. 
NOW IT WORKS! 
([explanation that someone posted before is here]("http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/comment-page-3/"))

thanks hans!

Hey, how did you contact Hans? I have a wevcam with upsidedown image and would really like to get it fixed too. Can you PM me his contact info.

---

### Post by HansdeGoede on 2009-12-21
> **mikewhatever said:**
> Hey, how did you contact Hans? I have a wevcam with upsidedown image and would really like to get it fixed too. Can you PM me his contact info.

You can mail me at [email]hdegoede@redhat.com[/email], I will need the log files generated by the following 2 commands:
lsusb > lsusb.log
dmidecode > dmi.log

The last command needs to be executed as root. Please send me a mail with the 2 files attached, do not copy paste them, I need to have them 100% unmodified and copy and paste may modify them.

Regards,

Hans

---

### Post by mikewhatever on 2009-12-21
> **HansdeGoede said:**
> You can mail me at [email]hdegoede@redhat.com[/email], I will need the log files generated by the following 2 commands:
lsusb > lsusb.log
dmidecode > dmi.log

The last command needs to be executed as root. Please send me a mail with the 2 files attached, do not copy paste them, I need to have them 100% unmodified and copy and paste may modify them.

Regards,

Hans

Thanks for answering. I didn't know you were visiting here often, should have just posted the files here. Anyway, I'll do both now, thanks again.

---

### Post by phikai on 2009-12-21
Hans thanks for doing all this! I emailed you the files, so hopefully you'll be able to take a look! Thanks again for all the work and support on this...can't wait for Skype to work properly for me...

---

### Post by someNewb on 2009-12-21
> **mikewhatever said:**
> Hey, how did you contact Hans? I have a wevcam with upsidedown image and would really like to get it fixed too. Can you PM me his contact info.
dude, it was all in the link i posted

> **HansdeGoede said:**
> You can mail me at ...  if i were you, i would **not** write my mail adress in clean text format just like that ..spambots are really evil

---

### Post by HansdeGoede on 2009-12-22
> **someNewb said:**
> if i were you, i would **not** write my mail adress in clean text format just like that ..spambots are really evil

Hehe,

Thanks for the concern, but given that my mail address is in the copy right headers / ChangeLog for a dozen or more opensource projects, and that I post to dozens of foss mailinglist with it, I'm sure every spambot in the world already has it (comes with the territory I'm afraid).

Regards,

Hans

---

### Post by phikai on 2009-12-22
Thanks Hans for getting me the new files, worked like a charm! Have the Horizontal flip issue still...but I think I saw something about that a couple pages back...

---

### Post by phikai on 2009-12-22
I installed v4l2ucp "sudo apt-get install v4l2ucp" but I don't have the horizontal flip option... any suggestions on this?

---

### Post by HansdeGoede on 2009-12-22
> **phikai said:**
> I installed v4l2ucp "sudo apt-get install v4l2ucp" but I don't have the horizontal flip option... any suggestions on this?

Try
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so v4l2ucp
most likely ubuntu's v4l2ucp is not compiled with libv4l support.

Regards,

Hans

---

### Post by phikai on 2009-12-22
> **HansdeGoede said:**
> Try
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so v4l2ucp
most likely ubuntu's v4l2ucp is not compiled with libv4l support.

Regards,

Hans

Wow...more helpful than any one person should be, THANKS! Until Skype decides to fix their issue with the flipped image (since cheese doesn't have this issue...I'm assuming its a Skype only thing) Is there a way to add a hflip to the start up script for skype?

---

### Post by mikewhatever on 2009-12-22
> **HansdeGoede said:**
> Try
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so v4l2ucp
most likely ubuntu's v4l2ucp is not compiled with libv4l support.

Regards,

Hans

I got the vertical/horisontal flip options with that and, having applied the horisontal flip got the image displaying correctly in both cheese and skype. Wow, thanks a lot.

---

### Post by HansdeGoede on 2009-12-23
> **phikai said:**
> Wow...more helpful than any one person should be, THANKS! Until Skype decides to fix their issue with the flipped image (since cheese doesn't have this issue...I'm assuming its a Skype only thing) Is there a way to add a hflip to the start up script for skype?

v4l2ucp also has a cmdline utility v4l2ctrl, which can save / restore settings, you could use that to switch between different sets of settings.

Regards,

Hans

---

### Post by someNewb on 2009-12-23
> **phikai said:**
> Wow...more helpful than any one person should be, THANKS! Until Skype decides to fix their issue with the flipped image (since cheese doesn't have this issue...I'm assuming its a Skype only thing) Is there a way to add a hflip to the start up script for skype? i don't know if it can be called as "issue", it just doesn't use v4l2

---

### Post by phikai on 2009-12-23
> **HansdeGoede said:**
> v4l2ucp also has a cmdline utility v4l2ctrl, which can save / restore settings, you could use that to switch between different sets of settings.

Regards,

Hans

AWESOME! That worked great...loaded up v4l2ucp and did the horizontal flip switch... then I saved the config using the v4l2ctrl command line utility. So now my launcher script for skype is:

```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so v4l2ctrl -d /dev/video0 -l ~/Config/webcam_skype.cfg
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

That loads the config file with the horizontal flip and loads skype using the v4l files. Thanks for all the help!

---

### Post by therox on 2009-12-26
Oh Hans, you are so awesome!!! libv4l-0.6.4-test works for my Asus X50SL with:
```
Bus 001 Device 003: ID 174f:5a35 Syntek Sonix 1.3MPixel USB 2.0 Camera
```After hundreds Forums I finally arrived!!
Man, you rock! :guitar:

greets, therox

---

### Post by abandonedthe_mulletator on 2009-12-28
Thanks to Hans I got the image un-fliped.  :guitar:

Now when I use the webcam in skype or vlc the program crashes.  I was able to test it using gstreamer-properties from the command line.

Here's some info:
ASUS K60 laptop
Ubuntu 9.10 (2.6.31-14-generic)
I followed Hans instructions in this thread

Here's the command line output from VLC:
```
VLC media player 1.0.2 Goldeneye
[0x1dd0db8] main interface error: no interface module matched "globalhotkeys,none"
[0x1dd0db8] main interface error: no suitable interface module
[0x1cbc888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x1cbc888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
/home/ng/.themes/Clearlooks-Warning/gtk-2.0/gtkrc:62: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 132.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  101
  Current serial number in output stream:  102

```

Any ideas?

---

### Post by abandonedthe_mulletator on 2009-12-28
OK, I found a workaround for VLC but not skype.  In VLC I disabled "embed video in interface" and opened it with the command line with ```
LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so vlc

```

Then the webcam is right side up and does not crash.  I need the webcam for skype though.  If I run skype from the command line it gives me this:
```
LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib64/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes) 

```

I get the same output if I load skype with:
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype 
```

---

### Post by HansdeGoede on 2009-12-29
> **the_mulletator said:**
> OK, I found a workaround for VLC but not skype.  In VLC I disabled "embed video in interface" and opened it with the command line with ```
LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so vlc

```

Then the webcam is right side up and does not crash.  I need the webcam for skype though.  If I run skype from the command line it gives me this:
```
LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib64/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes) 

```

I get the same output if I load skype with:
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype 
```

Hi,

I'm afraid this seems to be an issue with your xorg installation and / or video driver. Not much I can do there I'm afraid.

Regards,

Hans

---

### Post by abandonedthe_mulletator on 2009-12-29
It turns out this is a problem with the cairo-dock.  But if I load skype (or VLC) with this command the error goes away.
```
export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so skype

```

The image is still flipped in skype ](*,)

I tried changing ```
LD_PRELOAD=/usr/[COLOR="red"]lib64[/COLOR]/libv4l/v4l1compat.so
to 
LD_PRELOAD=/usr/[COLOR="Red"]lib32[/COLOR]/libv4l/v41compat.so 
and
LD_PRELOAD=/usr/[COLOR="Red"]lib[/COLOR]/libv4l/v4l1compat.so
```

.../usr/lib32/...  gave me an error but .../usr/lib/... did not.:confused:

Also my webcam is not reconized in cheese but it works fine using gstreamer-properties. :confused:

So, a very strange situation here.  Any ideas on how to get skype to cooperate?

---

### Post by HansdeGoede on 2009-12-29
> **the_mulletator said:**
> It turns out this is a problem with the cairo-dock.  But if I load skype (or VLC) with this command the error goes away.
```
export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so skype

```

The image is still flipped in skype ](*,)

I tried changing ```
LD_PRELOAD=/usr/[COLOR="red"]lib64[/COLOR]/libv4l/v4l1compat.so
to 
LD_PRELOAD=/usr/[COLOR="Red"]lib32[/COLOR]/libv4l/v41compat.so 
and
LD_PRELOAD=/usr/[COLOR="Red"]lib[/COLOR]/libv4l/v4l1compat.so
```

.../usr/lib32/...  gave me an error but .../usr/lib/... did not.:confused:

Also my webcam is not reconized in cheese but it works fine using gstreamer-properties. :confused:

So, a very strange situation here.  Any ideas on how to get skype to cooperate?

I think you only did a 64 bit build of libv4l, which won't work as skype is 32 bit.

Remove all copies of libv4l, to start with a clean slate:

rm -fr /usr/lib*/libv4l* /usr/local/lib*/libv4l*

Then download:
[http://people.fedoraproject.org/~jwrdegoede/libv4l-0.6.4-test.tar.gz](http://people.fedoraproject.org/~jwrdegoede/libv4l-0.6.4-test.tar.gz)

And install according to these instructions (and follow them exactly!):
[http://hansdegoede.livejournal.com/7622.html](http://hansdegoede.livejournal.com/7622.html)

Regards,

Hans

---

### Post by abandonedthe_mulletator on 2009-12-29
That did the trick.  Thank you Hans.  The command to run skype is this:
```
export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by Taires Bayl on 2010-01-03
hello,


i am new and therefor fast with problems. Now i tried to patch my webcam and everything went well up to this point:

> 
[SIZE=2]Then:
     Code:
     sudo make install
sudo cp uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/
sudo cp uvcvideo.ko /lib/modules/`uname -r`/usb/media/
sudo depmod -ae
sudo modprobe -f uvcvideo 
[/SIZE]
The problem is the error that there is no file named uvcvideo.ko and so i am stuck nearly finish and do not know what to do.

thanks, Taires
[SIZE=2]
 
[/SIZE]

---

### Post by Steini666 on 2010-01-10
Hi,

I got recently an ASUS K70IJ-TY041L Notebook and have the same problem with the upside down image. The Output of lsusb and dmidecode:

Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC WebCam / CNF7129


Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: ASUSTeK Computer Inc.        
	Product Name: K70IJ     
	Version: 1.0       
	Serial Number: BSN12345678901234567
	Asset Tag: ATN12345678901234567
	Features:
		Board is a hosting board
		Board requires at least one daughter board
		Board is replaceable
	Location In Chassis: MIDDLE              
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

greetinx

Andy

---

### Post by HansdeGoede on 2010-01-10
> **Steini666 said:**
> Hi,

I got recently an ASUS K70IJ-TY041L Notebook and have the same problem with the upside down image. The Output of lsusb and dmidecode:

Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC WebCam / CNF7129


Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: ASUSTeK Computer Inc.        
	Product Name: K70IJ     
	Version: 1.0       
	Serial Number: BSN12345678901234567
	Asset Tag: ATN12345678901234567
	Features:
		Board is a hosting board
		Board requires at least one daughter board
		Board is replaceable
	Location In Chassis: MIDDLE              
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

greetinx

Andy


Hi,

That laptop is already known to the latest libv4l:
[http://people.fedoraproject.org/~jwrdegoede/libv4l-0.6.4-test.tar.gz](http://people.fedoraproject.org/~jwrdegoede/libv4l-0.6.4-test.tar.gz)

Installation instructions here:
[http://hansdegoede.livejournal.com/7622.html](http://hansdegoede.livejournal.com/7622.html)

Regards,

Hans

---

### Post by gotaserena on 2010-01-26
Hello,

I've just got one of these netbooks with a built-in webcamera. I've also found out that the image is rotated 180 degrees and tried to re-compile libv4l to fix this. I've found that the way to go is to include the vendor and model information in the source of libv4lconvert/libv4lconvert.c. I would be very thankful if someone would teach me how to extract the necessary info from the output of lsusb and dmidecode.

The webcamera is listed as ```
ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC WebCam / CNF7129
```. Does anybody know whether this has been added to the newest/trunk/mercurial libv4l?

TIA

---

### Post by HansdeGoede on 2010-01-26
> **gotaserena said:**
> Hello,

I've just got one of these netbooks with a built-in webcamera. I've also found out that the image is rotated 180 degrees and tried to re-compile libv4l to fix this. I've found that the way to go is to include the vendor and model information in the source of libv4lconvert/libv4lconvert.c. I would be very thankful if someone would teach me how to extract the necessary info from the output of lsusb and dmidecode.

The webcamera is listed as ```
ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC WebCam / CNF7129
```. Does anybody know whether this has been added to the newest/trunk/mercurial libv4l?

TIA

Hi,

Just do (as root):
lsusb > lsusb.log
dmidecode > dmi.log

And send me <hdegoede@redhat.com>, a mail with these 2 files attached. Do *NOT* copy and paste them I need them 100% unmodified.

I'll then add your laptop to libv4l's upside down table and get back to you with testing instructions.

Regards,

Hans

---

### Post by gotaserena on 2010-01-26
Hi Hans, I've just sent you the files. Thank you very much!

---

### Post by thematrixuum on 2010-02-21
I'm having problem to patch the file. Do I have to rename the file to .patch file? Because I am stuck here :

```
patch < patch_solution1_mirrored.txt 
The program 'patch' is currently not installed.  You can install it by typing:
sudo apt-get install patch
patch: command not found

```Anything I done wrong?

BTW, I'm a noob.. Only a four day experience in Linux and Ubuntu..

---

### Post by paalfe on 2010-03-05
Is this still the best/only solution to fix Upside-down image from UVC webcam running ubuntu 9.10?

what happens with the fix when kernel or packages is updated?
Do I have to do the fix again then?

---

### Post by paalfe on 2010-03-06
Found this fine solution and wanted to share it:

[http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam]("http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam")

**quick howto:**

```

sudo add-apt-repository ppa:libv4l
sudo aptitude update && sudo aptitude install gtk-v4l libv4l-0

```


If ubuntu 32bit, do:
```

sudo su
echo -e '#!/bin/sh\nLD_PRELOAD=/usr/lib/libv4l/v4l1compat.so $1\nexit 0' > /bin/webcamWrapper
chmod +x /bin/webcamWrapper
exit

```

If ubuntu 32bit, you can now run programs like this to fix webcam upside-down image:
```

webcamWrapper skype
webcamWrapper amsn

```


If ubuntu 64bit, do:
```

sudo su
echo -e '#!/bin/sh\nLD_PRELOAD=/usr/lib/libv4l/v4l1compat.so $1\nexit 0' > /bin/webcamWrapper
echo -e '#!/bin/sh\nLD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so $1\nexit 0' > /bin/webcamWrapper32
chmod +x /bin/webcamWrapper
chmod +x /bin/webcamWrapper32
exit

```

If ubuntu 64bit, you can now run programs like this to fix webcam upside-down image:
```

webcamWrapper32 skype
webcamWrapper amsn

```

---

### Post by Random_Dude on 2010-03-27
I've tried the solution in the first post and the one in the post above, none of them worked.

After my attempt with the first, my pc stopped detecting the camera. Then I opened synaptic and reinstalled almost everything that said video driver (and probably the kernel).
I rebooted and opened chesse, the image was no longer upside down, but skype still has that problem.

So 50% of my problem is fixed, does anyone know how to flip the image in skype? :lol:

---

### Post by fakhri on 2010-04-01
> **paalfe said:**
> Found this fine solution and wanted to share it:

[http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam]("http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam")

**quick howto:**

```

sudo add-apt-repository ppa:libv4l
sudo aptitude update && sudo aptitude install gtk-v4l libv4l-0

```


If ubuntu 32bit, do:
```

sudo su
echo -e '#!/bin/sh\nLD_PRELOAD=/usr/lib/libv4l/v4l1compat.so $1\nexit 0' > /bin/webcamWrapper
chmod +x /bin/webcamWrapper
exit

```

If ubuntu 32bit, you can now run programs like this to fix webcam upside-down image:
```

webcamWrapper skype
webcamWrapper amsn

```


If ubuntu 64bit, do:
```

sudo su
echo -e '#!/bin/sh\nLD_PRELOAD=/usr/lib/libv4l/v4l1compat.so $1\nexit 0' > /bin/webcamWrapper
echo -e '#!/bin/sh\nLD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so $1\nexit 0' > /bin/webcamWrapper32
chmod +x /bin/webcamWrapper
chmod +x /bin/webcamWrapper32
exit

```

If ubuntu 64bit, you can now run programs like this to fix webcam upside-down image:
```

webcamWrapper32 skype
webcamWrapper amsn

```

it works it works!! The solution on the first post didn't work for me. I added a blank line at the end of the patch, yet it still came out with error.

I'm using karmic on ASUS K40IN. The uvc device id is 04f2:b071.

Thanks for the solution!!:D

---

### Post by ItalOz on 2010-04-06
> **paalfe said:**
> Found this fine solution and wanted to share it:


the solution that paalfe has proposed

[http://ubuntuforums.org/showthread.php?p=8925031#post8925031]("http://ubuntuforums.org/showthread.php?p=8925031#post8925031")

worked perfectly on my wife's brand new ASUS K50IJ the webcam model after issuing ```
lsusb
``` is
```
Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC WebCam / CNF7129
```

I think this marks the end of horrible windows 7 in this laptop, when she bought it she was really pissed of how slow the system was with the new computer and that sometimes because windows wanted to install updates without asking (default behaviour) the computer hang for ages before actually turned off.

So I saw a chance and I went "how about jumping to linux dear?" so far...

Cheers to everybody

---

### Post by Random_Dude on 2010-04-06
> **paalfe said:**
> Found this fine solution and wanted to share it:

[http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam)


My bad, this one works. I didn't made the last command. :biggrin:
It's much simpler than the one on the first post.

Thanks paalfe!

Cheers.;)

---

### Post by drewVeidt on 2010-04-29
Unfortunately, linking to the /usr/lib32/libv4l/v4l1compat.so just causes skype to segfault when i go to test the camera.  I'm on a 64 bit Asus K52J.  I didn't think that would matter since the 32 bit library is installed, but I guess it does.

I may be down to building uvcvideo myself, which seems like a pretty horrific option.  Especially considering that the code is no longer hosted in the manner in which the solution publishes (it's over 2 years old and the codebase has been reorganized and relocated).  If anybody has further advice on this, it'd be great.  Otherwise I guess I'll just have to figure it out on my own and then share it so the next clown doesn't have to deal with it!

The only thing I know about the cam is that it is by "IMC Networks."

---

### Post by drewVeidt on 2010-04-29
I do not have the option to flip in v4l2ucp

---

### Post by drewVeidt on 2010-04-29
> **drewVeidt said:**
> Unfortunately, linking to the /usr/lib32/libv4l/v4l1compat.so just causes skype to segfault when i go to test the camera.  I'm on a 64 bit Asus K52J.  I didn't think that would matter since the 32 bit library is installed, but I guess it does.

I may be down to building uvcvideo myself, which seems like a pretty horrific option.  Especially considering that the code is no longer hosted in the manner in which the solution publishes (it's over 2 years old and the codebase has been reorganized and relocated).  If anybody has further advice on this, it'd be great.  Otherwise I guess I'll just have to figure it out on my own and then share it so the next clown doesn't have to deal with it!

The only thing I know about the cam is that it is by "IMC Networks."

I've forwarded Hans the information he requests, so hopefully my laptop is just not recognized by libv4l1.  I am using an Asus K52J with an "IMC Networks" webcam.

---

### Post by Ev1L on 2010-05-21
hi, i am trying to flip the image in skype.
if i start simply skype, it's bottom up.
if i start: LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
it is correct.

#locate libv4lconvert
/usr/include/libv4lconvert.h
/usr/lib/libv4lconvert.so
/usr/lib/libv4lconvert.so.0
/usr/lib/pkgconfig/libv4lconvert.pc
/usr/local/include/libv4lconvert.h
/usr/local/lib/pkgconfig/libv4lconvert.pc

isn't there a way to make it a default?

---

### Post by Arminho on 2010-05-27
It took me a while to fix this problem with my new ASUS K50AF running Lucid (32 Bit Version).
Finally the following approach worked - I hope this description will save you some time:

1. Check if the wrapper helps your application
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so <your application>
``` (e.g. ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```)
If yes, continue as suggested in  [http://ubuntuforums.org/showpost.php...&postcount=225]("http://ubuntuforums.org/showpost.php...&postcount=225") (create the wrapper & use it to call the app).
If no, continue as follows:

2. Download current libv4l Sources (I used Version 0.8.0)
2.a Download from [http://freshmeat.net/projects/libv4l](http://freshmeat.net/projects/libv4l)
2.b Unpack to your Home-Dir (e.g. ~/v4l-utils-0.8.0/)

3. Identify your Webcam & Board
3.a. ```
lsusb
``` to get the device ID (Format (hex) <XXXX>:<YYYY>)
BUS ddd Device ddd: ID XXXX:YYYY Your Webcam
3.b. Create a file containing the Board Vendor Name (e.g. vendor.txt)
```
cat /sys/devices/virtual/dmi/id/board_vendor > vendor.txt
```
3.c. Create a file containing the Board Name (e.g. name.txt)
```
cat /sys/devices/virtual/dmi/id/board_name > name.txt
```

4. Update the Upside Down list of libv4l
4.a Open the control-File from the Source Folder in an ASCII editor (e.g. ```
gedit ~/v4l-utils-0.8.0/lib/libv4lconvert/control/libv4lcontrol.c
```)
4.b. The file contains the list of "Upside down devices" at the start. Add the entry for your Configuration:
	```
{ 0x<XXXX>, 0x<YYYY>, 0, <VENDOR>, <NAME>,
		V4LCONTROL_HFLIPPED | V4LCONTROL_VFLIPPED },
```
Where: 	<XXXX> and <YYYY> is the ID of your webcam from lsusb
	<VENDOR> is the content of vendor.txt (wioth all white spaces !!)
	<NAME> is the content of vendor.txt (with all white spaces !!)

# 5. Compile and Install libv4l
5.a. enter the lib-source directory (e.g. ```
cd ~/v4l-utils-0.8.0/lib
```
5.b. ```
sudo make clean
```
5.c. ```
sudo make PREFIX=/usr
```
5.d. ```
sudo make install PREFIX=/usr
```

6. Test the result
6.a. Start your application. If the image is correct now, the application uses libv4l. If not continue
6.b. Try the Wrapper: ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so <your application>
``` (e.g. ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```) If the image is still upside-down be careful to doublecheck Vendor, Name and ID (everything is case sensitive AND whitespaces are important).
6.c. Alternatively (I did not try this option) you may use the control panel (System->Settings->Video4Linux or Applications->Media->Video4Linux Device Properties). In some versions this panel includes a "Horizontal Flip"-checkbox.

---

### Post by Archatos on 2010-06-02
Arminho, thank you for your solution!

It works on my Asus K70AF. Thank you very much, you just made me very happy! :D

Uhhh... this brings up another question: How do I make this permanent? I wouldn't like to start my apps with LD_PRELOAD ......... Any idea?

---

### Post by bander013 on 2010-06-14
UL30VT with 064e:a136 Suyin Corp.

My combination already in libv4l Sources Version 0.8.0.

I'm preloading library but it still not flipped. Occasionally I Have found absence of 'dmi' folder in my '/sys/devices/virtual'.

I'm not sure but can it be a reason why it not working? Maybe libv4l reading info from there (not from dmidecode)?

PS:I'm gentoo user

---

### Post by bander013 on 2010-06-14
Yep, as I thought X)

Go to kernel src:
```
cd /usr/src/linux && sudo make menuconfig
```

Search for DMI:
```
/dmi
```

You need this:
```
Symbol: DMIID [=y]
Prompt: Export DMI identification via sysfs to userspace
Defined at drivers/firmware/Kconfig:106
Depends on: DMI [=y]
Location:
-> Firmware Drivers

```

This thing must be enabled to make tutor from previous work. ):P

---

### Post by Arminho on 2010-06-17
> **Archatos said:**
> Arminho, thank you for your solution!

It works on my Asus K70AF. Thank you very much, you just made me very happy! :D

Uhhh... this brings up another question: How do I make this permanent? I wouldn't like to start my apps with LD_PRELOAD ......... Any idea?

My pleasure, Archatos!
I used the webcamWarapper-solution described in [http://ubuntuforums.org/showpost.php?p=8925031&postcount=225]("http://ubuntuforums.org/showpost.php?p=8925031&postcount=225") to make the settings permanent for skype. For cheese (and all other apps that use libv4l) there is no need to use the wrapper.

Please also inform Hans de Goede (hdegoede@redhat.com) about the changes that worked for you..he maintains the relevant part of lib4vl. This will make sure that others will not have the same problem with ASUS K70AF in the future.

---

### Post by frmdstryr on 2010-06-29
> **paalfe said:**
> Found this fine solution and wanted to share it:

[http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam]("http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam")

**quick howto:**

```

sudo add-apt-repository ppa:libv4l
sudo aptitude update && sudo aptitude install gtk-v4l libv4l-0

```


If ubuntu 32bit, do:
```

sudo su
echo -e '#!/bin/sh\nLD_PRELOAD=/usr/lib/libv4l/v4l1compat.so $1\nexit 0' > /bin/webcamWrapper
chmod +x /bin/webcamWrapper
exit

```

If ubuntu 32bit, you can now run programs like this to fix webcam upside-down image:
```

webcamWrapper skype
webcamWrapper amsn

```


If ubuntu 64bit, do:
```

sudo su
echo -e '#!/bin/sh\nLD_PRELOAD=/usr/lib/libv4l/v4l1compat.so $1\nexit 0' > /bin/webcamWrapper
echo -e '#!/bin/sh\nLD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so $1\nexit 0' > /bin/webcamWrapper32
chmod +x /bin/webcamWrapper
chmod +x /bin/webcamWrapper32
exit

```

If ubuntu 64bit, you can now run programs like this to fix webcam upside-down image:
```

webcamWrapper32 skype
webcamWrapper amsn

```

Thank you!!  Fixed my Asus UL30A-A2

---

### Post by vanadium on 2010-07-16
Another thank you to Arminho! Only five beans at the time of writing, but it are super ones!
For me, it concerns an Asus PRO5EA
```
"ASUSTeK Computer Inc.        ", "K51AE     "
```

---

### Post by zatja on 2010-07-24
> **arjos85 said:**
> [FONT=Arial][SIZE=2]Hi everybody,
it's a very quick how-to that will help you to solve the problem of those webcams who give back upside-down images/videos!!!
This help is intended only for those who have a UVC capable webcam.
But it will be usefull only if your webcam supports YUV image format and the applications that use your webcam request YUV format to your webcam!!! I've tested it and it works with:
skype, amsn, kopete, luvcview, mplayer!!

So...let's start!!!!

In order to know if your webcam is UVC capable you just need to open your shell and run:
[/SIZE][/FONT][SIZE=2]```
lsusb
```[/SIZE][FONT=Arial][SIZE=2]
you will get something like this:
Then type:
[/SIZE][/FONT][SIZE=2]```
sudo lsusb -d xxxx:yyyy -v | grep "14 Video"
```[/SIZE][FONT=Arial][SIZE=2]
If you get something like the following, your webcam is UVC capable:
[/SIZE][/FONT][SIZE=2][/SIZE][FONT=Arial][SIZE=2]
If your webcam passes this test, you can go on reading. Otherwise, your camera needs to use propertary driver, because it doesn't use standard protocol/command.

Well,
now you need to donwload the UVCVIDEO driver sources, but they are on a SVN repository, so you need to install the SVN client:
[/SIZE][/FONT][SIZE=2]```
sudo apt-get install subversion
```[/SIZE][FONT=Arial][SIZE=2]and now you can download the sources:
[/SIZE][/FONT][SIZE=2]```
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
```[/SIZE][FONT=Arial][SIZE=2]
The sources will be saved into a folder called "Trunk" in the path from where you run the previous command.

Now there are 2 solutions, please try both and tell me which one you think is the  best!!

[B][COLOR=Red]Now for both solutions there are two patches: the former gives back mirrored images, the latter NOT mirrored images.
[/COLOR][COLOR=Red]You have to copy one of them into "Trunk" folder in a file (called for example "uvc_video_solution1.patch"), and then from terminal go into the "Trunk" folder and do:
[/COLOR][/B][/SIZE][/FONT][SIZE=2]**[COLOR=Red]```
patch < uvc_video_solution1.patch
```WARNING: each of the following patch refers to the original "uvc_video.c" file, so before applying a new patch be sure that the "uvc_video.c" file[/COLOR]**[/SIZE][SIZE=2]**[COLOR=Red] in "Trunk" folder[/COLOR]**[/SIZE][SIZE=2][B][COLOR=Red] is the original one. So please remember to backup the original file.
[/COLOR][/B][/SIZE] [FONT=Arial][COLOR=Red][SIZE=2] 
[B]_WARNING:_
YOU HAVE TO ADD A BLANK LINE AT THE END OF EACH PATCH IN ORDER TO SUCCEED THE PATCHING!!

[U]NEWS:
[/U]NOW YOU CAN DOWNLOAD THE PATCHES AND DON'T NEED ANY MORE TO ADD A NEW LINE!!!
TAKE A LOOK AT THE BOTTOM OF THIS HOW-TO, YOU WILL FIND 4 PATCHES, JUST CHOOSE THE ONE YOU PREFER AND DONWLOAD IT!![/B]   ;)

_[COLOR=Blue]**WARNING: Patches available in this HowTo refer to the UVC driver version 0.1.0, so if you install a different version you will have to apply the patch by hand!!!**[/COLOR]_

**_FIRST SOLUTION (MIRRORED IMAGES)_**
[/SIZE][/COLOR][/FONT][FONT=Arial][SIZE=2][COLOR=Red]# modified June 26, 2008[/COLOR]
[/SIZE][/FONT]```
diff -uN UVCVIDEO_v0.1.0/uvc_video.c UVCVIDEO_patched/uvc_video.c
--- UVCVIDEO_v0.1.0/uvc_video.c    2008-06-26 10:41:01.000000000 +0200
+++ UVCVIDEO_patched/uvc_video.c    2008-06-26 15:33:33.000000000 +0200
@@ -371,23 +371,92 @@
     return data[0];
 }
 
+/* This patched function allows to overturn video images from an upside-down
+ * orientation to a normal one with mirrored effect. The conversion simply
+ * consists in reversing the order of the rows of imagines.
+ * This patch performs its job just once for each frame and only when current
+ * frame is completed, but each time it is required to allocate memory in order
+ * to store a copy of that frame.
+ * This patch should work with all YUV image formats.
+ */
 static void uvc_video_decode_data(struct uvc_video_device *video,
         struct uvc_buffer *buf, const __u8 *data, int len)
 {
     struct uvc_video_queue *queue = &video->queue;
     unsigned int maxlen, nbytes;
     void *mem;
+    /* Patch variables */
+    __u8 *mem_tmp, *ptr_tmp;
+    int i, k, row_size;
 
     if (len <= 0)
         return;
 
     /* Copy the video data to the buffer. */
+    /* How many bytes are needed to complete the buffer? */
     maxlen = buf->buf.length - buf->buf.bytesused;
+    /* Where do pixels stored in "data" have to be copied? */
     mem = queue->mem + buf->buf.m.offset + buf->buf.bytesused;
+    /* How many bytes really can be copied into "mem"? */
     nbytes = min((unsigned int)len, maxlen);
+    /* "nbytes" are copied from "data" to "mem" buffer.
+     * "data" stores a sequence of pixels coming from the video source.
+     * This sequence is not a full frame or a full row of pixel, but just an
+     * ordered vector of pixels (from top-left to bottom-right), whose
+     * represents just an area of the current frame.
+     * This function has to be called hundreds of times before a frame is
+     * completed and "nbytes" is not constant! Each time "data" contains the
+     * next part of the frame. At the end data stored in "mem" buffer will
+     * be used by the application who requested the video stream.
+     */
     memcpy(mem, data, nbytes);
     buf->buf.bytesused += nbytes;
 
+    /* Have the last copied bytes completed the current frame? */
+    if (nbytes == maxlen) {
+        /* Area where to save the upper half part of the original frame
+         * (just half in order to speed up the patch) before reversing.
+         */
+        mem_tmp = (__u8 *) kmalloc(buf->buf.bytesused / 2, GFP_ATOMIC);
+        if (mem_tmp != NULL ) {
+            /* Copy top-half part of frame in a temporary buffer */
+            memcpy(mem_tmp, queue->mem + buf->buf.m.offset,
+                   buf->buf.bytesused / 2);
+            /* "row_size" does not depend only on the width of the
+             * frame, but also on the pixel color depth (bpp).
+             */
+            row_size = video->streaming->cur_frame->wWidth *
+                   video->streaming->format->bpp / 8;
+            /* The following cycle just copy full frame rows from
+             * the last one stored in "mem" (and going up) to the
+             * first one (and going down) stored in "mem" itself.
+             */
+            ptr_tmp = queue->mem + buf->buf.m.offset
+                  + buf->buf.bytesused / 2;
+            /* When the top-half of the frame has been reversed,
+             * rows are copied from the last one stored in "mem_tmp"
+             * (and going up) into the bottom half part of "mem"
+             * buffer.
+             */
+            for (i = 0, k = buf->buf.bytesused / 2 - row_size;
+                 i < buf->buf.bytesused;
+                 i += row_size, k -= row_size) {
+                /* If the top-half of the frame has been
+                 * revesed, then it is needed to split the
+                 * source buffer from "mem" to "mem_tmp".
+                 */
+                if (i == buf->buf.bytesused / 2) {
+                    ptr_tmp = mem_tmp;
+                    k = buf->buf.bytesused / 2 - row_size;
+                }
+                memcpy(queue->mem + buf->buf.m.offset + i,
+                       ptr_tmp + k,
+                       row_size);
+            }
+            /* For this frame "mem_tmp" is not needed any more. */
+            kfree(mem_tmp);
+        }
+    }
     /* Complete the current frame if the buffer size was exceeded. */
     if (len > maxlen) {
         uvc_trace(UVC_TRACE_FRAME, "Frame complete (overflow).\n");


```[SIZE=4]
[/SIZE][FONT=Arial][SIZE=2][U]
[B][COLOR=Red]FIRST SOLUTION ([SIZE=5]NOT[/SIZE] MIRRORED IMAGES)
[/COLOR][/B][/U][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Red]# modified June 26, 2008[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Red]
[/COLOR][/SIZE][/FONT]```

diff -uN UVCVIDEO_v0.1.0/uvc_video.c UVCVIDEO_patched/uvc_video.c
--- UVCVIDEO_v0.1.0/uvc_video.c    2008-06-26 10:41:01.000000000 +0200
+++ UVCVIDEO_patched/uvc_video.c    2008-06-26 15:33:33.000000000 +0200
@@ -371,23 +371,105 @@
     return data[0];
 }
 
+/* This patch should work ONLY with YUY2 image formats, also known as YUYV or
+ * YUV422 formats.
+ * This patched function allows to overturn video images from an upside-down
+ * orientation to a normal one. The conversion consists in copying 4 bytes at a
+ * time (Y0,U0,Y1,V0) corresponding to 2 pixels, in a bottom-up direction, from
+ * the frame (coming from the video source) to the buffer that will be used by
+ * the application requesting the video stream. But in order to satisfy the YUY2
+ * image format byte has to be copied in this way: Y1 U0 Y0 VO.
+ * This patch performs its job just once for each frame and only when current
+ * frame is completed, but each time it is required to allocate memory in order
+ * to store a copy of that frame.
+ */
 static void uvc_video_decode_data(struct uvc_video_device *video,
         struct uvc_buffer *buf, const __u8 *data, int len)
 {
     struct uvc_video_queue *queue = &video->queue;
     unsigned int maxlen, nbytes;
     void *mem;
+    /* Patch variables */
+    __u8 *mem_tmp, *ptr_tmp;
+    int i, k, pixel_size;
 
     if (len <= 0)
         return;
 
     /* Copy the video data to the buffer. */
+    /* How many bytes are needed to complete the buffer? */
     maxlen = buf->buf.length - buf->buf.bytesused;
+    /* Where do pixels stored in "data" have to be copied? */
     mem = queue->mem + buf->buf.m.offset + buf->buf.bytesused;
+    /* How many bytes really can be copied into "mem"? */
     nbytes = min((unsigned int)len, maxlen);
+    /* "nbytes" are copied from "data" to "mem" buffer.
+     * "data" stores a sequence of pixels coming from the video source.
+     * This sequence is not a full frame or a full  row of pixel, but just
+     * an ordered vector of pixels (from top-left to bottom-right), whose
+     * represents just an area of the current frame.
+     * This function has to be called hundreds of times before a frame is
+     * completed and "nbytes" is not constant! Each time "data" contains the
+     * next part of the frame. At the end data stored in "mem" buffer will
+     * be used by the application who requested the video stream.
+     */
     memcpy(mem, data, nbytes);
     buf->buf.bytesused += nbytes;
 
+    /* Have the last copied bytes completed the current frame? */
+    if (nbytes == maxlen) {
+        /* Area where to save the original frame before manipulation. */
+        mem_tmp = (__u8 *) kmalloc(buf->buf.bytesused / 2, GFP_ATOMIC);
+        if (mem_tmp != NULL ) {
+            /* Copy the original frame in a temporary buffer. */
+            memcpy(mem_tmp, queue->mem + buf->buf.m.offset,
+                   buf->buf.bytesused / 2);
+            /* "pixel_size" depens on the pixel color depth (bpp),
+             * but in YUY2 image format is constant and equal to 2.
+             */
+             pixel_size = video->streaming->format->bpp / 8;
+            /* The following loop copy 2 pixels at a time (4 bytes
+             * in YUY2 format) from the last two stored in "mem"
+             * (and going back) to the first two (and going on)
+             * stored in "mem" itself following a sort of YUY2
+             * algorithm.
+             */
+            ptr_tmp = queue->mem + buf->buf.m.offset
+                  + buf->buf.bytesused / 2;
+            /* When the top-half of the frame has been reversed,
+             * rows are copied from the last one stored in "mem_tmp"
+             * (and going up) into the bottom half part of "mem"
+             * buffer.
+             */
+            for (i = 0, k = buf->buf.bytesused / 2 - 2 * pixel_size;
+                 i < buf->buf.bytesused;
+                 i += 2 * pixel_size, k -= 2 * pixel_size){
+                /* If the top-half of the frame has been
+                 * revesed, then it is needed to split the
+                 * source buffer from "mem" to "mem_tmp".
+                 */
+                if (i == buf->buf.bytesused / 2) {
+                    ptr_tmp = mem_tmp;
+                    k = buf->buf.bytesused / 2
+                        - 2 * pixel_size;
+                }
+                 /* The order of copied bytes is changed from
+                  * (Y0 U0 Y1 V1) to (Y1 U0 Y0 V1), i.e. from
+                  * (#0 #1 #2 #3) to (#2 #1 #0 #3).
+                  */
+                 ((__u8 *)(queue->mem+buf->buf.m.offset + i))[0] =
+                 ((__u8 *)(ptr_tmp + k))[2];
+                 ((__u8 *)(queue->mem+buf->buf.m.offset + i))[1] =
+                 ((__u8 *)(ptr_tmp + k))[1];
+                 ((__u8 *)(queue->mem+buf->buf.m.offset + i))[2] =
+                 ((__u8 *)(ptr_tmp + k))[0];
+                 ((__u8 *)(queue->mem+buf->buf.m.offset + i))[3] =
+                 ((__u8 *)(ptr_tmp + k))[3];
+            }
+            /* For this frame "mem_tmp" is not needed any more. */
+            kfree(mem_tmp);
+        }
+    }
     /* Complete the current frame if the buffer size was exceeded. */
     if (len > maxlen) {
         uvc_trace(UVC_TRACE_FRAME, "Frame complete (overflow).\n");



```[FONT=Arial][SIZE=2][U][COLOR=Red][B]
SECOND SOLUTION (MIRRORED IMAGES)[/B][/COLOR][/U]
[/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Red]# modified June 26, 2008[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Red]
[/COLOR][/SIZE][/FONT]```

diff -uN UVCVIDEO_v0.1.0/uvc_video.c UVCVIDEO_patched/uvc_video.c
--- UVCVIDEO_v0.1.0/uvc_video.c    2008-06-26 10:41:01.000000000 +0200
+++ UVCVIDEO_patched/uvc_video.c    2008-06-26 14:03:58.000000000 +0200
@@ -371,23 +371,91 @@
     return data[0];
 }
 
+/* This patched function allows to overturn video images from an upside-down
+ * orientation to a normal one with mirrored effect. The conversion consists in
+ * reversing the order of the rows of imagines.
+ * "data" stores a sequence of pixels coming from the video source.
+ * This sequence is not a full frame or a full row of pixel, but just an
+ * ordered vector of pixels (from top-left to bottom-right), whose
+ * represents just an area of the current frame and which size ("nbytes") is
+ * not constant. In fact this function has to be called hundreds of times
+ * before a frame is completed. Each time "data" contains the next part of the
+ * current frame (upside-down). At the end data stored in "mem" buffer will be
+ * used by the application who requested the video stream.
+ * No memory allocation is needed because pixel order is modified directly
+ * while copying from "data" into "mem" buffer (i.e. in each call of this
+ * function), and not just once when the frame is already completed.
+ * This patch should work with all YUV image formats.
+ */
 static void uvc_video_decode_data(struct uvc_video_device *video,
         struct uvc_buffer *buf, const __u8 *data, int len)
 {
     struct uvc_video_queue *queue = &video->queue;
     unsigned int maxlen, nbytes;
     void *mem;
+    /* Patch variables */
+    unsigned int row_size, to_be_copied, shift_right;
 
     if (len <= 0)
         return;
 
     /* Copy the video data to the buffer. */
+    /* How many bytes are needed to complete the buffer? */
     maxlen = buf->buf.length - buf->buf.bytesused;
+    /* Where do pixels stored in "data" have to be copied? */
     mem = queue->mem + buf->buf.m.offset + buf->buf.bytesused;
+    /* How many bytes really can be copied into "mem"? */
     nbytes = min((unsigned int)len, maxlen);
-    memcpy(mem, data, nbytes);
-    buf->buf.bytesused += nbytes;
 
+    /* "row_size" is the number of bytes required to store a full row of
+     * the frame.
+     */
+    row_size = video->streaming->cur_frame->wWidth *
+           video->streaming->format->bpp / 8;
+    /* Each loop "nbytes" is decremented of the number of bytes just copied.
+     * So are there any other bytes to be copied?
+     */
+    while (nbytes > 0) {
+        /* As the rows of modified frames have to be fulfilled from
+         * bottom-left to top-right, each cycle tries to complete a
+         * single row.
+         * In this cycle where is it needed to start to store bytes
+         * within the selected row? From the beginning or shifted
+         * right? Because other bytes could have been already stored in
+         * that row without completing it, so it could be needed a right
+         * shift.
+         */
+        shift_right = buf->buf.bytesused % row_size;
+        /* In this cycle how many byte can we copy in the selected row?
+         */
+        if (nbytes > row_size - shift_right)
+            to_be_copied = row_size - shift_right ;
+        else
+            to_be_copied = nbytes;
+        /* "queue->mem + buf->buf.m.offset" is the base-address where to
+         * start to store the current frame. This address refers to a
+         * preallocated area (just for a sigle frame) taking part in a
+         * circular buffer, where to store a fixed number of sequent
+         * frames.
+         */
+        memcpy(queue->mem + buf->buf.m.offset
+               /* Go to the end of this frame. */
+               + row_size * video->streaming->cur_frame->wHeight
+               /* Go back for the number of bytes corrisponding to the
+                * already fully completed rows.
+            */
+               - (buf->buf.bytesused - shift_right)
+               /* Go back at the starting point of the upper row. */
+               - row_size
+               /* Shift right on this row if it is needed. */
+               + shift_right,
+               data,
+               to_be_copied );
+        /* Update "data", "byteused" and "nbytes" values. */
+        data += to_be_copied;
+        buf->buf.bytesused += to_be_copied ;
+        nbytes -= to_be_copied;
+    }
     /* Complete the current frame if the buffer size was exceeded. */
     if (len > maxlen) {
         uvc_trace(UVC_TRACE_FRAME, "Frame complete (overflow).\n");



```[FONT=Arial][SIZE=2][U][B][COLOR=Red]
SECOND SOLUTION ([SIZE=5]NOT[/SIZE] MIRRORED IMAGES)
[/COLOR][/B][/U][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Red]# modified June 26, 2008[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Red]
[/COLOR][/SIZE][/FONT]```

diff -uN UVCVIDEO_v0.1.0/uvc_video.c UVCVIDEO_patched/uvc_video.c
--- UVCVIDEO_v0.1.0/uvc_video.c    2008-06-26 10:41:01.000000000 +0200
+++ UVCVIDEO_patched/uvc_video.c    2008-06-26 14:03:58.000000000 +0200
@@ -371,23 +371,81 @@
     return data[0];
 }
 
+/* This patch should work ONLY with YUY2 image formats, also known as YUYV or
+ * YUV422 formats.
+ * This patched function allows to overturn video images from an upside-down
+ * orientation to a normal one. The conversion consists in copying 4 bytes at a
+ * time (Y0,U0,Y1,V0) corresponding to 2 pixels from the frame (coming from the
+ * video source) to the buffer that will be used by the application requesting
+ * the video stream. But in order to satisfy the YUY2 image format byte has to
+ * be copied in this way: Y1 U0 Y0 VO. Bytes are copied in a bottom-up
+ * direction into the reversed frame.
+ * "data" stores a sequence of pixels coming from the video source.
+ * This sequence is not a full frame or a full row of pixel, but just an
+ * ordered vector of pixels (from top-left to bottom-right), whose
+ * represents just an area of the current frame and which size ("nbytes") is
+ * not constant. In fact this function has to be called hundreds of times
+ * before a frame is completed. Each time "data" contains the next part of the
+ * current frame (upside-down). At the end data stored in "mem" buffer will be
+ * used by the application who requested the video stream.
+ * No memory allocation is needed because pixel order is modified directly
+ * while copying from "data" into "mem" buffer (i.e. in each call of this
+ * function), and not just once when the frame is already completed.
+ */
 static void uvc_video_decode_data(struct uvc_video_device *video,
         struct uvc_buffer *buf, const __u8 *data, int len)
 {
     struct uvc_video_queue *queue = &video->queue;
     unsigned int maxlen, nbytes;
     void *mem;
+    /* Patch variables */
+    unsigned int i, pixel_size;
+    __u8 *ptr_tmp;
 
     if (len <= 0)
         return;
 
     /* Copy the video data to the buffer. */
+    /* How many bytes are needed to complete the buffer? */
     maxlen = buf->buf.length - buf->buf.bytesused;
+    /* Where do pixels stored in "data" have to be copied? */
     mem = queue->mem + buf->buf.m.offset + buf->buf.bytesused;
+    /* How many bytes really can be copied into "mem"? */
     nbytes = min((unsigned int)len, maxlen);
-    memcpy(mem, data, nbytes);
-    buf->buf.bytesused += nbytes;
 
+    /* "pixel_size" depens on the pixel color depth (bpp),
+     * but in YUY2 image format is constant and equal to 2.
+     */
+    pixel_size = video->streaming->format->bpp / 8;
+    /* In each loop 4 bytes are modified and copied into "mem" buffer. */
+    for (i = 0; i < nbytes; i += 2 * pixel_size) {
+            /* "queue->mem + buf->buf.m.offset" is the base-address
+             * where to start to store the current frame. This
+             * address refers to a preallocated area (just for a
+             * sigle frame) taking part in a circular buffer, where
+             * to store a fixed number of sequent frames.
+             */    
+        ptr_tmp = (__u8 *)(queue->mem + buf->buf.m.offset
+            /* Go to the end of this frame. */
+            + video->streaming->cur_frame->wWidth * pixel_size
+            * video->streaming->cur_frame->wHeight
+            /* Go back for the number of already copied bytes. */
+            - buf->buf.bytesused
+            /* Go back for the number of bytes (4 bytes) to be
+             *  copied in this cycle.
+             */
+            - 2 * pixel_size);
+        /* The order of copied bytes is changed from
+         * (Y0 U0 Y1 V1) to (Y1 U0 Y0 V1), i.e. from
+         * (#0 #1 #2 #3) to (#2 #1 #0 #3).
+         */
+        ptr_tmp[0] = ((__u8 *)(data + i))[2];
+        ptr_tmp[1] = ((__u8 *)(data + i))[1];
+        ptr_tmp[2] = ((__u8 *)(data + i))[0];
+        ptr_tmp[3] = ((__u8 *)(data + i))[3];
+        /* Update "byteused" value. */
+        buf->buf.bytesused += 2 * pixel_size;
+    }
     /* Complete the current frame if the buffer size was exceeded. */
     if (len > maxlen) {
         uvc_trace(UVC_TRACE_FRAME, "Frame complete (overflow).\n");



```~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[SIZE=2]

Well, now the worst part has been done!!!
We just need to compile our modded file and to install the new driver, so from shell you have to go to the "Trunk" directory and type:
[/SIZE]```
make
```[SIZE=2]there shouldn't be errors!!

[/SIZE][SIZE=2]Then, ONLY if you are using one of the Ubuntu distributions (ubuntu, kubuntu, etc.), open with you editor the "Makefile" and change the following line:
[/SIZE]```
INSTALL_MOD_DIR := usb/media
```[SIZE=2]with
[/SIZE]```
INSTALL_MOD_DIR := ubuntu/media/usbvideo
```[SIZE=2]Now we just need to remove uvcvideo module (if you have previously installed it):
[/SIZE][SIZE=2]```
sudo modprobe -r uvcvideo
```Then:
```

sudo make install
sudo cp uvcvideo.ko /lib/modules/`uname -r`/ubuntu/media/usbvideo/
sudo cp uvcvideo.ko /lib/modules/`uname -r`/usb/media/
sudo depmod -ae
sudo modprobe -f uvcvideo

```Now everything should work!!!

Let me know!!

And please try both solutions..
in case you don't see any difference just use the **[COLOR=Red]SECOND[/COLOR]** solution (mirrored or not, has you prefer), it should be the safest!!

Good luck,
enjoy your webcam!! ;)

Arjos85 :guitar:

ps. excuse me for this too quick HOW-TO, without good explainations, but really just right now I haven't time to do it more verbose!!!
pps. excuse me also in case I made some mistakes!!!
[/SIZE]
Hello Arjos85
I have tried to launch script you have provided but obtained this message.

zatja@zatja-NB-Ubu:~$ svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
svn: No repository found in 'svn://svn.berlios.de/linux-uvc/linux-uvc/trunk'
zatja@zatja-NB-Ubu:~$ 

Pls, help.
Thanks 
Jaromir

---

### Post by rt-2 on 2010-07-29
```
rt-2@rt-2:~$ svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
svn: No repository found in 'svn://svn.berlios.de/linux-uvc/linux-uvc/trunk'

```

the source is down

---

### Post by g.oostema on 2010-08-02
> **paalfe said:**
> Found this fine solution and wanted to share it:

[http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam)

**quick howto:**

```

sudo add-apt-repository ppa:libv4l
sudo aptitude update && sudo aptitude install gtk-v4l libv4l-0

```
If ubuntu 32bit, do:
```

sudo su
echo -e '#!/bin/sh\nLD_PRELOAD=/usr/lib/libv4l/v4l1compat.so $1\nexit 0' > /bin/webcamWrapper
chmod +x /bin/webcamWrapper
exit

```If ubuntu 32bit, you can now run programs like this to fix webcam upside-down image:
```

webcamWrapper skype
webcamWrapper amsn

```
If ubuntu 64bit, do:
```

sudo su
echo -e '#!/bin/sh\nLD_PRELOAD=/usr/lib/libv4l/v4l1compat.so $1\nexit 0' > /bin/webcamWrapper
echo -e '#!/bin/sh\nLD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so $1\nexit 0' > /bin/webcamWrapper32
chmod +x /bin/webcamWrapper
chmod +x /bin/webcamWrapper32
exit

```If ubuntu 64bit, you can now run programs like this to fix webcam upside-down image:
```

webcamWrapper32 skype
webcamWrapper amsn

```

tnx for the solution, works fine in skype. gyachi was already good and so is kopete and cheese.

however running msn with the wrapper command still gives me an upside down camera.
anyone any options???

---

### Post by g.oostema on 2010-08-03
> **HansdeGoede said:**
> Hi,

Just do (as root):
lsusb > lsusb.log
dmidecode > dmi.log

And send me <hdegoede@redhat.com>, a mail with these 2 files attached. Do *NOT* copy and paste them I need them 100% unmodified.

I'll then add your laptop to libv4l's upside down table and get back to you with testing instructions.

Regards,

Hans
hand 
i tried the above command but get the following error:

giliam@giliam-laptop:~$ lsusb > lsusb.log
giliam@giliam-laptop:~$ dmidecode > dmi.log
/dev/mem: Permission denied
giliam@giliam-laptop:~$ dmidecode
# dmidecode 2.9
/dev/mem: Permission denied

Can you help me, i would love my cam in the list as right now it is still upside down in amsn.

tnx

giliam

---

### Post by Halfling Rogue on 2010-08-08
Source down.

svn: No repository found in 'svn://svn.berlios.de/linux-uvc/linux-uvc/trunk'

---

### Post by Jaz969 on 2010-08-29
> **g.oostema said:**
> hand 
i tried the above command but get the following error:

giliam@giliam-laptop:~$ lsusb > lsusb.log
giliam@giliam-laptop:~$ dmidecode > dmi.log
/dev/mem: Permission denied
giliam@giliam-laptop:~$ dmidecode
# dmidecode 2.9
/dev/mem: Permission denied

Can you help me, i would love my cam in the list as right now it is still upside down in amsn.

tnx

giliam

dmidecode requires root access

Do this instead:

sudo dmidecode > dmi.log

---

### Post by RDT1 on 2010-09-14
svn: No repository found in 'svn://svn.berlios.de/linux-uvc/linux-uvc/trunk'

Source still down. Anyone know of  mirror?

---

### Post by Beholder87 on 2010-09-27
Problem here:
I am using a Asus UL30A series laptop. And the webcam works fine on skype, but when I use the gmail's video chat, the image is flipped upside down. I installed libv4l-0, but it didn't change anything to the video. Can I get some help?
Ps: I'm not using kubuntu, but Ubuntu 10.04 LTS

---

### Post by Boy1dr on 2010-09-27
Beholder87
You might want to check wheter or not you a starting you Skype with the 'webcamwrapper.sh' script.

If you are not using that script, check whether the camera is correct displayed, when you do not have the libv4l-0 package installed. (the problem might have been fixed, which mean that you are actually flipping an already flipped video in Gmail's video chat ...and that Skype is using the original package)

---

### Post by Beholder87 on 2010-10-03
> **Boy1dr said:**
> Beholder87
You might want to check wheter or not you a starting you Skype with the 'webcamwrapper.sh' script.

If you are not using that script, check whether the camera is correct displayed, when you do not have the libv4l-0 package installed. (the problem might have been fixed, which mean that you are actually flipping an already flipped video in Gmail's video chat ...and that Skype is using the original package)

In my skype the video is normal, but in gmail, it is fliped upside down. So this is what I did: installed v4l2ucp. When I select the option in the program: horizontal flip or vertical flip, the image flips on skype, but not in gmail. Changing the options in the program doesn't change anything in gmail. 

In gmail and skype and in the v4l2ucp it ssays that my webcam is a usb, however it is a buil-in camera in the laptop (not a usb plugged in). Maybe what I have to do is to find the correct video driver and install it. (But it doesn't make sense for me that skype works normally, but gmail doesn't... (And I tested it both on chromium and firefox to check the gmail)

---

### Post by Boy1dr on 2010-10-04
Skype and most other simular software running directly in Ubuntu, is using the v4l (Video4Linux layer) ... therefore Skype has no issues in regards to flip the cam upside down, using the v4l-settings software.

GMail however is using its own way to connect to the webcam, thereby bypassing the v4l-layer.  Therefore the video remains upside down.

In regards to the way the camera is connected...
Most webcams in a laptop are connected through the USB-system ....there are internal connectors as well as external.  The webcams obviously are using the internal ones (usual sockets that are available on the motherboard)

---

### Post by dugh on 2010-10-07
There is no horizontal or vertical flip option in the v4l2ucp control panel.

Using an Asus N61J (N61JV)

---

### Post by HansdeGoede on 2010-10-08
Hi All,

> **Arminho said:**
> It took me a while to fix this problem with my new ASUS K50AF running Lucid (32 Bit Version).
Finally the following approach worked - I hope this description will save you some time:

<snip>


To all: if you fix things this way, please still do the following (as root):
lsusb > lsusb.log
dmidecode > dmi.log

And send me <hdegoede@redhat.com>, a mail with these 2 files attached. Do *NOT* copy and paste them I need them 100% unmodified.

I'll then add your laptop permanently to libv4l's upside down table, so that other people using the same laptop (and you yourself when updating to a newer distro version) don't need to fix things manually, but instead everything will work out of the box!!

Arminho if you communicate with people about this solution please ask them to send their laptop info to me so I can permanently add there model to libv4l's upside down list.

Regards,

Hans de Goede (the libv4l author and maintainer)

---

### Post by HansdeGoede on 2010-10-08
> **zatja said:**
> Hello Arjos85
I have tried to launch script you have provided but obtained this message.

zatja@zatja-NB-Ubu:~$ svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
svn: No repository found in 'svn://svn.berlios.de/linux-uvc/linux-uvc/trunk'
zatja@zatja-NB-Ubu:~$ 

Pls, help.
Thanks 
Jaromir

Hi,

Please do not use the orginal patch your kernel solution, it:

1) Is very painful to do for you as a user
2) Won't help anyone else with the same laptop model
3) Needs to be redone each kernel update / re-install
4) Will also flip images of any external uvc webcam plugged into your laptop.

Instead you should get the latest libv4l which has a (constantly updated) list of know to have an upside down webcam laptop models. Installation instructions are here:
[http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/)

If that does not work your laptop model is not in the list of libv4l, please do (as root):
lsusb > lsusb.log
dmidecode > dmi.log

And send me <hdegoede@redhat.com>, a mail with the 2 generated files attached. Do *NOT* copy and paste them I need them 100% unmodified.

I'll then add your laptop to libv4l's upside down table and get back to you with testing instructions.

Regards,

Hans

---

### Post by HansdeGoede on 2010-10-08
> **Halfling Rogue said:**
> Source down.

svn: No repository found in 'svn://svn.berlios.de/linux-uvc/linux-uvc/trunk'

Hi,

Please do not use the orginal patch your kernel solution, it:

1) Is very painful to do for you as a user
2) Won't help anyone else with the same laptop model
3) Needs to be redone each kernel update / re-install
4) Will also flip images of any external uvc webcam plugged into your laptop.

Instead you should get the latest libv4l which has a (constantly updated) list of know to have an upside down webcam laptop models. Installation instructions are here:
[http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/)

If that does not work your laptop model is not in the list of libv4l, please do (as root):
lsusb > lsusb.log
dmidecode > dmi.log

And send me <hdegoede@redhat.com>, a mail with the 2 generated files attached. Do *NOT* copy and paste them I need them 100% unmodified.

I'll then add your laptop to libv4l's upside down table and get back to you with testing instructions.

Regards,

Hans

---

### Post by HansdeGoede on 2010-10-08
> **RDT1 said:**
> svn: No repository found in 'svn://svn.berlios.de/linux-uvc/linux-uvc/trunk'

Source still down. Anyone know of  mirror?

Hi,

Please do not use the orginal patch your kernel solution, it:

1) Is very painful to do for you as a user
2) Won't help anyone else with the same laptop model
3) Needs to be redone each kernel update / re-install
4) Will also flip images of any external uvc webcam plugged into your laptop.

Instead you should get the latest libv4l which has a (constantly updated) list of know to have an upside down webcam laptop models. Installation instructions are here:
[http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/)

If that does not work your laptop model is not in the list of libv4l, please do (as root):
lsusb > lsusb.log
dmidecode > dmi.log

And send me <hdegoede@redhat.com>, a mail with the 2 generated files attached. Do *NOT* copy and paste them I need them 100% unmodified.

I'll then add your laptop to libv4l's upside down table and get back to you with testing instructions.

Regards,

Hans

---

### Post by HansdeGoede on 2010-10-08
> **Boy1dr said:**
> Skype and most other simular software running directly in Ubuntu, is using the v4l (Video4Linux layer) ... therefore Skype has no issues in regards to flip the cam upside down, using the v4l-settings software.


That is not entirely correct the flip functionality for uvc webcams is handled in userspace through libv4l. Most apps shipped with a modern Linux distro use libv4l. For some reason most proprietary apps don't. You don't notice that skype is not using libv4l, as ubunutu ships it with a wrapper script which uses the libv4l provided c-library shim which intercepts the relevant calls and redirects them to libv4l.

> **Boy1dr said:**
> 
GMail however is using its own way to connect to the webcam, thereby bypassing the v4l-layer.  Therefore the video remains upside down.


The google video chat plugin is also not using libv4l but accessing the device directly. I've tried contacting google about this, but I've gotten 0 response. Using LD_PRELOAD with the libv4l compat wrapper .so is not really an option here as the plugin gets loaded from firefox.

Please mail google and ask them *kindly* to start using libv4l, also let them know they are free to mail me with any questions at Hans de Goede <hdegoede@redhat.com>

Regards,

Hans (the libv4l author and maintainer)

---

### Post by HansdeGoede on 2010-10-08
> **dugh said:**
> There is no horizontal or vertical flip option in the v4l2ucp control panel.

Using an Asus N61J (N61JV)

Hi,

Try using the latest libv4l which has a (constantly updated) list of know to have an upside down webcam laptop models. Installation instructions are here:
[http://radu.cotescu.com/2009/11/05/f...ubuntu-webcam/](http://radu.cotescu.com/2009/11/05/f...ubuntu-webcam/)

If that does not work your laptop model is not in the list of libv4l, please do (as root):
lsusb > lsusb.log
dmidecode > dmi.log

And send me <hdegoede@redhat.com>, a mail with the 2 generated files attached. Do *NOT* copy and paste them I need them 100% unmodified.

I'll then add your laptop to libv4l's upside down table and get back to you with testing instructions.

Regards,

Hans

---

### Post by Dr.C on 2010-12-31
Having installed a 'Buntu derivative on my wife's newly-gifted Asus K601 Notebook, I was dismayed when she reported that her Skype image was flipped.  Owing to the info obtained from this thread, the problem has been corrected. Thanks for all the help; especially that of Hans de Goede! 

My first deliberately employed script reads:
[I]  #!/bin/bash
  export LIBV4LCONTROL_FLAGS=3
  LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype[/I]

Happy New Year,
Chard in Oregon

---

### Post by itsazebra on 2011-02-10
Thanks to HansdeGoede, the webcam on my ASUS U3JC "Bamboo" works allright now. :)
Thank you very much!

Edit: I don't know what's the problem after reboot, but the cam is flipped upside down again (in skype)... :( Has anybody an idea what went wrong ? 

Regards,
itsazebra.

---

### Post by pejoslav on 2011-05-15
I cant believe that there is no simple solution to flip image on laptop camera...i googled for 15 minutes - and every single 'fix' is just too complicated for a regular user. Why is there no setting/app with button which says FLIP and thats it...not user friendly :(

---

### Post by HansdeGoede on 2011-05-17
> **pejoslav said:**
> I cant believe that there is no simple solution to flip image on laptop camera...i googled for 15 minutes - and every single 'fix' is just too complicated for a regular user. Why is there no setting/app with button which says FLIP and thats it...not user friendly :(

Hi,

The reason there is no quick solution is because the flipping needs to be done in software, which adds an extra processing step to the the video pipeline even when flipping is not used. This comes with a significant performance penalty, esp. with modern cameras doing high resolutions like 1920x1080. I see no reason to penalize all Linux users with lower performance / higher battery use, because some laptop manufacturers (Asus mostly) insist on putting the webcam the wrong way up in the display bezel. If you want to complain, complain to Asus.

Also I don't want the user to simply need to select a flip option, I want things to work correctly without any user intervention at all. This is why libv4l contains a table with identification strings for laptop models which are known to have their camera upside down. So for most users things just work.

You likely have either an old libv4l, or your laptop still needs to be added to said table. Once your laptop is in the table, not only will your webcam work for you, but for all people with the same model laptop.

You can find instructions for getting a newer libv4l, and if that does not help how to send me the info I need to add your laptop to the table here:
[http://ubuntuforums.org/showpost.php?p=9938564&postcount=254](http://ubuntuforums.org/showpost.php?p=9938564&postcount=254)

Regards,

Hans de Goede (libv4l author and maintainer)

---

### Post by soylentcola on 2011-06-16
If this is still being updated...is there a way to get this to flip online applications? (For example, going to a website that lets you use a webcam?) I only ask because otherwise, my camera is still flipped upside down. :(

---

### Post by dugh on 2011-06-20
Any solution to fixing the upside down video in google talk / gmail ?  

The webcamWrapper fixes it for Skype and other tools, but not gmail.  I saw the earlier explanation that Chrome/Chromium and the like are using a different method to access the video, but I was just wonder if anyone found a fix.

Thanks

---

### Post by Halfling Rogue on 2011-06-20
I did it by changing the Launcher properties for Firefox [as per the instructions here]("http://radu.cotescu.com/flipped-images-ubuntu-webcam/").

Set up the .sh file following the directions in the link and then paste this in the Command box for the Firefox Launcher:

```
webcamWrapper.sh firefox %u
```

That'll run the webcam patch whenever you run Firefox, which should enable the flipping for all browser-related cam apps.

---

### Post by aparrales on 2011-07-10
This solution worked for me.
laptop Siragon SL-6120, Ubuntu 10.10

Thanks a lot

---

### Post by oldarney on 2011-07-29
> **Halfling Rogue said:**
> I did it by changing the Launcher properties for Firefox [as per the instructions here]("http://radu.cotescu.com/flipped-images-ubuntu-webcam/").

Set up the .sh file following the directions in the link and then paste this in the Command box for the Firefox Launcher:

```
webcamWrapper.sh firefox %u
```That'll run the webcam patch whenever you run Firefox, which should enable the flipping for all browser-related cam apps.

Thanks for the firefox patch.
Add Google+ to the list of non libv4l users. I wish there was a hardware hack to fix that. Why not just distribute a better driver for asus computers... it's done for alot of non webcam hardware.

---

### Post by insane9 on 2011-08-22
ian@ubuntu:~$ svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
svn: No repository found in 'svn://svn.berlios.de/linux-uvc/linux-uvc/trunk'

^^^

got the following error message. Any ideas?

---

### Post by kpike on 2011-09-15
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk

returns

svn: No repository found in 'svn://svn.berlios.de/linux-uvc/linux-uvc/trunk'

Is there any updated source available?

---

### Post by Megastar12 on 2011-09-15
[LEFT][COLOR=#556E8B][FONT=verdana]Hello Mark. I would check for an updated driver for your webcam on Asus's support site here: [ASUSTeK Computer Inc.-Support-]("http://support.asus.com/download/download.aspx")

Make sure you are also using the authentic SP2 with the number "6001.18000.080118-1840" in it's file name for the 'ISO" number, or the upgrade redistributal directly from MS's download/update websites. I've installed the SP on a number of systems, both laptop and system towers with no problems so far.

:popcorn::p:p:p


[Watch TV Online]("http://www.goonlinetv.com")
[URL="http://www.goonlinetv.com"]watch online tv 
[/URL]
[/FONT][/COLOR][/LEFT]

---

### Post by paalfe on 2012-06-18
This is how I fix the webcam upside/down problem now, ubuntu 12.04.
I use skype as an example!


Some webcams works perfect with Cheese and other webcam applications, but in Skype you may have a green screen, no picture at all or the picture is upside down!
If you have webcam issues with skype, fix this by doing this:

```
echo -e '#!/bin/bash \n LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype' | sudo tee /usr/local/bin/skype
sudo chmod a+x /usr/local/bin/skype
```

**NOTE1:** Skype is a 32bit program so i386 in the above fix is correct for skype since it uses 32bit libraries, even if you use 64bit version of Ubuntu!

**NOTE2:** If the program you want to manipulate is 64bit you have to use **/usr/lib/x86_64-linux-gnu/libv4l/** instead of **/usr/lib/i386-linux-gnu/libv4l/**

If the above fix does not work, try using this instead
```
echo -e '#!/bin/bash \n LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so /usr/bin/skype' | sudo tee /usr/local/bin/skype
```

---

### Post by tahitiwibble on 2012-07-17
> **HansdeGoede said:**
> Hi All,



To all: if you fix things this way, please still do the following (as root):
lsusb > lsusb.log
dmidecode > dmi.log

And send me <hdegoede@redhat.com>, a mail with these 2 files attached. Do *NOT* copy and paste them I need them 100% unmodified.

I'll then add your laptop permanently to libv4l's upside down table, so that other people using the same laptop (and you yourself when updating to a newer distro version) don't need to fix things manually, but instead everything will work out of the box!!

Arminho if you communicate with people about this solution please ask them to send their laptop info to me so I can permanently add there model to libv4l's upside down list.

Regards,

Hans de Goede (the libv4l author and maintainer)


Thank you Hans!! Brilliant work!!

---

### Post by tahitiwibble on 2012-07-17
> **paalfe said:**
> This is how I fix the webcam upside/down problem now, ubuntu 12.04.
I use skype as an example!


Some webcams works perfect with Cheese and other webcam applications, but in Skype you may have a green screen, no picture at all or the picture is upside down!
If you have webcam issues with skype, fix this by doing this:

```
echo -e '#!/bin/bash \n LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype' | sudo tee /usr/local/bin/skype
sudo chmod a+x /usr/local/bin/skype
```

**NOTE1:** Skype is a 32bit program so i386 in the above fix is correct for skype since it uses 32bit libraries, even if you use 64bit version of Ubuntu!

**NOTE2:** If the program you want to manipulate is 64bit you have to use **/usr/lib/x86_64-linux-gnu/libv4l/** instead of **/usr/lib/i386-linux-gnu/libv4l/**

If the above fix does not work, try using this instead
```
echo -e '#!/bin/bash \n LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so /usr/bin/skype' | sudo tee /usr/local/bin/skype
```

Paalfe ....... thank you so much for posting [this]("http://ubuntuforums.org/showpost.php?p=8925031&postcount=225")

---

### Post by sdw003 on 2012-09-12
VLC saves the day, even if its not that intuitive. 

Open up VLC 2.0.3.
Click on the 6th button on the bottom left that looks like an equalizer, its the "show extended settings" button.
"Video Effect" Tab
"Geometry" Tab
Check "Rotate" checkbox and the dial becomes unghosted.
Rotate to desired angle.

That's all folks.

---

### Post by Jojojopo on 2012-12-08
> **paalfe said:**
> This is how I fix the webcam upside/down problem now, ubuntu 12.04.
I use skype as an example!


Some webcams works perfect with Cheese and other webcam applications, but in Skype you may have a green screen, no picture at all or the picture is upside down!
If you have webcam issues with skype, fix this by doing this:

```
echo -e '#!/bin/bash \n LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype' | sudo tee /usr/local/bin/skype
sudo chmod a+x /usr/local/bin/skype
```

**NOTE1:** Skype is a 32bit program so i386 in the above fix is correct for skype since it uses 32bit libraries, even if you use 64bit version of Ubuntu!

**NOTE2:** If the program you want to manipulate is 64bit you have to use **/usr/lib/x86_64-linux-gnu/libv4l/** instead of **/usr/lib/i386-linux-gnu/libv4l/**

If the above fix does not work, try using this instead
```
echo -e '#!/bin/bash \n LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so /usr/bin/skype' | sudo tee /usr/local/bin/skype
```

Man, I can't possibly thank you enough, I use skype all the time and this solved the issue for me. Thank you!

---

### Post by Dr._Daniel_James_White on 2013-08-31
ubuntu 13.04 32 bit
the two fixes above, is it relinking skype with the right video libs doesnt work for me. 
in skype and cheese , black image 
in camorama upside down image
i downloaded and built and installed the r5u87x driver as below


[COLOR=#000000][IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **Fictitious1** [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=11071105#post11071105")[/COLOR]
[COLOR=#000000][I]$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
$ hg clone [https://bitbucket.org/ahixon/r5u87x/]("http://bitbucket.org/ahixon/r5u87x/") *[I changed the link to reflect SSL]
$ cd r5u87x
$ make
$ sudo make install
$ sudo r5u87x-loader --reload

lsusb
Bus 001 Device 002: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]

so its the right device for that driver.... any clues?

[/I][/COLOR]

---

### Post by casper4 on 2013-09-22
I did this

> 
[COLOR=#000000]This is how I fix the webcam upside/down problem now, ubuntu 12.04.[/COLOR]
[COLOR=#000000]I use skype as an example![/COLOR]


[COLOR=#000000]Some webcams works perfect with Cheese and other webcam applications, but in Skype you may have a green screen, no picture at all or the picture is upside down![/COLOR]
[COLOR=#000000]If you have webcam issues with skype, fix this by doing this:[/COLOR]

[COLOR=#000000]Code:
echo -e '#!/bin/bash \n LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype' | sudo tee /usr/local/bin/skype
sudo chmod a+x /usr/local/bin/skype[/COLOR]
[B]NOTE1: Skype is a 32bit program so i386 in the above fix is correct for skype since it uses 32bit libraries, even if you use 64bit version of Ubuntu!

[B]NOTE2: If the program you want to manipulate is 64bit you have to use [B]/usr/lib/x86_64-linux-gnu/libv4l/ instead of [B]/usr/lib/i386-linux-gnu/libv4l/

If the above fix does not work, try using this instead
Code:
echo -e '#!/bin/bash \n LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so /usr/bin/skype' | sudo tee /usr/local/bin/skype
[/B][/B][/B][/B]

And now cam via flash in chrome is broken? it doesn't show anything?

also on my kubuntu 12.04 it say the following when i do this

```

casper@casper-UL30A:~$ svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
svn: No repository found in 'svn://svn.berlios.de/linux-uvc/linux-uvc/trunk'

```

Any correction made to the SVN url?
Any easy fix for cam with flash in chrome like there was with skype from above?
How to i find my lsusb.log and dmi.log files? i did a find but found nothing?

Thanks to all invovled with this for the great effort!

Casper

---

