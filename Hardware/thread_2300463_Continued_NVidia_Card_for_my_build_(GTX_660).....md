---
title: "Continued: NVidia Card for my build (GTX 660)...."
date: 2015-10-26
forum: Hardware
---

### Post by andrew.46 on 2015-10-26
[Previous thread]("http://ubuntuforums.org/showthread.php?t=2207500") closed down so I continue here :).

Took me a fair while to make this change so I eventually settled for an NVidia GeForce GTX 750 Ti which is now comfortably behind the cutting edge and now finally the graphics card matches the rest of the computer: a solid and fast work-horse that comfortably runs a few games as well :). Running the latest long-term NVidia drivers: 352.55...

---

### Post by Yellow Pasque on 2015-10-26
Does this bug affect you? [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-352/+bug/1500113](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-352/+bug/1500113)

---

### Post by andrew.46 on 2015-10-27
Indeed mc4man has eagle eyes :). My own log with 352.55:

```

andrew@ilium~$ vdpauinfo 
display: :0.0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  352.55  Thu Oct  8 14:52:18 PDT 2015

Video surface:

name   width height types
-------------------------------------------
420     4096  4096  NV12 YV12 
422     4096  4096  UYVY YUYV 

Decoder capabilities:

name                        level macbs width height
----------------------------------------------------
MPEG1                           0 65536  4080  4080
MPEG2_SIMPLE                    3 65536  4080  4080
MPEG2_MAIN                      3 65536  4080  4080
H264_BASELINE                  --- not supported ---
H264_MAIN                      41 65536  4096  4096
H264_HIGH                      41 65536  4096  4096
VC1_SIMPLE                      1  8190  2048  2048
VC1_MAIN                        2  8190  2048  2048
VC1_ADVANCED                    4  8190  2048  2048
MPEG4_PART2_SP                  3  8192  2048  2048
MPEG4_PART2_ASP                 5  8192  2048  2048
DIVX4_QMOBILE                   0  8192  2048  2048
DIVX4_MOBILE                    0  8192  2048  2048
DIVX4_HOME_THEATER              0  8192  2048  2048
DIVX4_HD_1080P                  0  8192  2048  2048
DIVX5_QMOBILE                   0  8192  2048  2048
DIVX5_MOBILE                    0  8192  2048  2048
DIVX5_HOME_THEATER              0  8192  2048  2048
DIVX5_HD_1080P                  0  8192  2048  2048
H264_CONSTRAINED_BASELINE      --- not supported ---
H264_EXTENDED                  --- not supported ---
H264_PROGRESSIVE_HIGH          --- not supported ---
H264_CONSTRAINED_HIGH          --- not supported ---
H264_HIGH_444_PREDICTIVE       --- not supported ---
HEVC_MAIN                      --- not supported ---
HEVC_MAIN_10                   --- not supported ---
HEVC_MAIN_STILL                --- not supported ---
HEVC_MAIN_12                   --- not supported ---
HEVC_MAIN_444                  --- not supported ---

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8         16384 16384    y  Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 
R10G10B10A2      16384 16384    y  Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 

Bitmap surface:

name              width height
------------------------------
B8G8R8A8         16384 16384
R8G8B8A8         16384 16384
R10G10B10A2      16384 16384
B10G10R10A2      16384 16384
A8               16384 16384

Video mixer:

feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     y
INVERSE_TELECINE                 y
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y
HIGH QUALITY SCALING - L1        y
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -

parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y         1     4096
VIDEO_SURFACE_HEIGHT             y         1     4096
CHROMA_TYPE                      y  
LAYERS                           y         0        4

attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y  


andrew@ilium~$ 

```

So I will try the 355.11 drivers and test again....

---

### Post by andrew.46 on 2015-10-27
vdpauinfo as follows for the newest driver:

```

andrew@ilium~$ vdpauinfo 
display: :0.0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  355.11  Wed Aug 26 16:05:52 PDT 2015

Video surface:

name   width height types
-------------------------------------------
420     4096  4096  NV12 YV12 
422     4096  4096  UYVY YUYV 

Decoder capabilities:

name                        level macbs width height
----------------------------------------------------
MPEG1                           0 65536  4080  4080
MPEG2_SIMPLE                    3 65536  4080  4080
MPEG2_MAIN                      3 65536  4080  4080
H264_BASELINE                  41 65536  4096  4096
H264_MAIN                      41 65536  4096  4096
H264_HIGH                      41 65536  4096  4096
VC1_SIMPLE                      1  8190  2048  2048
VC1_MAIN                        2  8190  2048  2048
VC1_ADVANCED                    4  8190  2048  2048
MPEG4_PART2_SP                  3  8192  2048  2048
MPEG4_PART2_ASP                 5  8192  2048  2048
DIVX4_QMOBILE                   0  8192  2048  2048
DIVX4_MOBILE                    0  8192  2048  2048
DIVX4_HOME_THEATER              0  8192  2048  2048
DIVX4_HD_1080P                  0  8192  2048  2048
DIVX5_QMOBILE                   0  8192  2048  2048
DIVX5_MOBILE                    0  8192  2048  2048
DIVX5_HOME_THEATER              0  8192  2048  2048
DIVX5_HD_1080P                  0  8192  2048  2048
H264_CONSTRAINED_BASELINE      41 65536  4096  4096
H264_EXTENDED                  41 65536  4096  4096
H264_PROGRESSIVE_HIGH          41 65536  4096  4096
H264_CONSTRAINED_HIGH          41 65536  4096  4096
H264_HIGH_444_PREDICTIVE       41 65536  4096  4096
HEVC_MAIN                      --- not supported ---
HEVC_MAIN_10                   --- not supported ---
HEVC_MAIN_STILL                --- not supported ---
HEVC_MAIN_12                   --- not supported ---
HEVC_MAIN_444                  --- not supported ---

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8         16384 16384    y  Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 
R10G10B10A2      16384 16384    y  Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 

Bitmap surface:

name              width height
------------------------------
B8G8R8A8         16384 16384
R8G8B8A8         16384 16384
R10G10B10A2      16384 16384
B10G10R10A2      16384 16384
A8               16384 16384

Video mixer:

feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     y
INVERSE_TELECINE                 y
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y
HIGH QUALITY SCALING - L1        y
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -

parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y         1     4096
VIDEO_SURFACE_HEIGHT             y         1     4096
CHROMA_TYPE                      y  
LAYERS                           y         0        4

attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y  


andrew@ilium~$ 

```

I would post on mc4man's bug report but this is not actually on Ubuntu :)

---

