---
title: "MPV h.265 hardware decoding issue"
date: 2016-02-04
forum: Hardware
---

### Post by gilles10 on 2016-02-04
Hello all,

Recently i purchased the nvidia GTX 960 (Zotac OC) in order to use hardware encoder/decoder capabilities for h.264 and h.265.
I installed the latest nvidia drivers and compiled libvdpau 1.1.1 by myself as it is recently no more part of nvidia distribution.

when i launch the following command : mpv --hwdec=vfpau --vo=opengl <h265filename>.mp4 I'm immediately falling-back to software decoding.

The h265 is properly hardware decoded under windows 10 by using media player classic HC through DVXA2 use. As only main profile is compatible with Nvidia card, I imagine the file is encoded with good profile.

when I type vdpauinfo I have the following:
```
display: :0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  361.18  Sat Jan  9 20:45:00 PST 2016

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
HEVC_MAIN                      153 36864  4096  2304
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
```

I am a little bit blocked at this point.
I would really appreciate the help of Ubuntu's masters. 

Thanks in advance for your help.
Gilles

---

### Post by howefield on 2016-02-04
Thread moved to the "*Hardware*" forum.

---

