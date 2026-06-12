---
title: "Sudden problem with printer"
date: 2012-07-04
forum: Hardware
---

### Post by mojo risin on 2012-07-04
Hi I have got a canon Ip90v pixma printer, and it used to work fine.
It is seen without a problem ```
morri@schrabbelkiste:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04a9:2220 Canon, Inc. CanoScan LIDE 25
Bus 004 Device 004: ID 04a9:109d Canon, Inc. iP90
Bus 005 Device 003: ID 057c:6201 AVM GmbH AVM Fritz!WLAN v1.1 [Texas Instruments TNETW1450]

``` and I havent had a problem, but now I have a problem which is , that the printer starts fine when I sent the order to print, but it stops already after only a few lines (15%) 
It sounds like it is stuck as the printer head always moves forwards and back about 1 cm.
When the power button is pressed it releases the paper, but the printer keep sflashing.
I have used the troubleshooter 
Heres the output.

```
age 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Is local server publishing?):
{'local_server_exporting_printers': False}
Page 3 (Choose printer):
{'cups_dest': <cups.Dest Canon-iP90 (default)>,
 'cups_instance': None,
 'cups_queue': 'Canon-iP90',
 'cups_queue_listed': True}
Page 4 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Canon/iP90?serial=574465',
                       'printer-info': u'Canon iP90',
                       'printer-is-shared': True,
                       'printer-location': u'schrabbelkiste',
                       'printer-make-and-model': u'Canon i80 - CUPS+Gutenprint v5.2.8-pre1',
                       'printer-state': 4,
                       'printer-state-message': u'Printing page 1, 35%',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 176140,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Canon-iP90'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.5.3',
                                 'device-uri': u'usb://Canon/iP90?serial=574465',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.adobe-reader-postscript',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-pdf-banner',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-raster',
                                                               u'application/vnd.cups-raw',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/x-bitmap',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': [u'en-us'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'ippget-event-life': 15,
                                 'job-creation-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'ipp-attribute-fidelity',
                                                                       u'job-hold-until',
                                                                       u'job-name',
                                                                       u'job-priority',
                                                                       u'job-sheets',
                                                                       u'media',
                                                                       u'media-col',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'output-bin',
                                                                       u'output-mode',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-ids-supported': True,
                                 'job-k-limit': 0,
                                 'job-k-octets-supported': (0, 24752472),
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-name',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'media-col',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'output-bin',
                                                                       u'output-mode',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'jpeg-k-octets-supported': (0, 24752472),
                                 'jpeg-x-dimension-supported': (0, 65535),
                                 'jpeg-y-dimension-supported': (1, 65535),
                                 'marker-change-time': 0,
                                 'media-bottom-margin-supported': [635, 1588],
                                 'media-col-supported': [u'media-bottom-margin',
                                                         u'media-left-margin',
                                                         u'media-right-margin',
                                                         u'media-size',
                                                         u'media-source',
                                                         u'media-top-margin',
                                                         u'media-type'],
                                 'media-default': u'na_letter_8.5x11in',
                                 'media-left-margin-supported': [388, 635],
                                 'media-right-margin-supported': [318, 635],
                                 'media-source-supported': [u'auto'],
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'na_legal_8.5x14in',
                                                     u'na_ledger_11x17in',
                                                     u'na_executive_7.25x10.5in',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'om_cd5-inch_116.06x116.06mm',
                                                     u'om_cd3-inch_64.91x64.91mm',
                                                     u'om_cdcustom_119.94x119.94mm',
                                                     u'oe_w216h360_3x5in',
                                                     u'oe_w252h360_3.5x5in',
                                                     u'oe_w288h432_4x6in',
                                                     u'om_w324h495_114.3x174.63mm',
                                                     u'iso_a6_105x148mm',
                                                     u'oe_w288h576_4x8in',
                                                     u'oe_w360h504_5x7in',
                                                     u'oe_w360h576_5x8in',
                                                     u'oe_w432h576_6x8in',
                                                     u'oe_c8x10_8x10in',
                                                     u'na_invoice_5.5x8.5in',
                                                     u'oe_w576h864_8x12in',
                                                     u'oe_w720h864-j_10x12in',
                                                     u'oe_w792h1008_11x14in',
                                                     u'iso_a3_297x420mm',
                                                     u'iso_a4_210x297mm',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a7_74x105mm',
                                                     u'iso_a8_52x74mm',
                                                     u'iso_a9_37x52mm',
                                                     u'iso_a10_26x37mm',
                                                     u'om_w609h864_214.84x304.8mm',
                                                     u'om_w637h907_224.72x319.97mm',
                                                     u'iso_b4_250x353mm',
                                                     u'iso_b5_176x250mm',
                                                     u'iso_b6_125x176mm',
                                                     u'iso_b7_88x125mm',
                                                     u'iso_b8_62x88mm',
                                                     u'jis_b9_45x64mm',
                                                     u'jis_b10_32x45mm',
                                                     u'jis_b4_257x364mm',
                                                     u'jis_b5_182x257mm',
                                                     u'jis_b6_128x182mm',
                                                     u'jis_b7_91x128mm',
                                                     u'jis_b8_64x91mm',
                                                     u'om_c4_228.95x323.85mm',
                                                     u'om_c5_161.93x228.95mm',
                                                     u'om_c5-l_228.95x161.93mm',
                                                     u'om_w354h918_124.88x323.85mm',
                                                     u'om_c6_113.95x161.93mm',
                                                     u'om_c6-l_161.93x113.95mm',
                                                     u'om_dl_109.71x219.78mm',
                                                     u'om_dl-l_219.78x109.71mm',
                                                     u'om_w229h459_80.79x161.93mm',
                                                     u'om_w229h459-l_161.93x80.79mm',
                                                     u'om_c7_80.79x113.95mm',
                                                     u'om_c7-l_113.95x80.79mm',
                                                     u'om_c8_56.8x80.79mm',
                                                     u'om_c8-l_80.79x56.8mm',
                                                     u'om_c9_39.86x56.8mm',
                                                     u'om_c9-l_56.8x39.86mm',
                                                     u'om_c10_27.87x39.86mm',
                                                     u'om_c10-l_39.86x27.87mm',
                                                     u'om_ea5_155.93x228.95mm',
                                                     u'om_ea5-l_228.95x155.93mm',
                                                     u'na_arch-a_9x12in',
                                                     u'oe_w612h936_8.5x13in',
                                                     u'oe_w648h936_9x13in',
                                                     u'om_w535h697_188.74x245.89mm',
                                                     u'om_w569h731_200.73x257.88mm',
                                                     u'om_w620h782_218.72x275.87mm',
                                                     u'om_w671h884_236.71x311.86mm',
                                                     u'om_w348h527_122.77x185.91mm',
                                                     u'om_w365h561_128.76x197.91mm',
                                                     u'om_w391h612_137.94x215.9mm',
                                                     u'om_w442h663_155.93x233.89mm',
                                                     u'om_w314h504_110.77x177.8mm',
                                                     u'om_w314h513_110.77x180.98mm',
                                                     u'om_w283h425_99.84x149.93mm',
                                                     u'om_w420h567_148.17x200.03mm',
                                                     u'om_w340h666_119.94x234.95mm',
                                                     u'om_w340h666-l_234.95x119.94mm',
                                                     u'om_w255h581_89.96x204.96mm',
                                                     u'om_w255h581-l_204.96x89.96mm',
                                                     u'om_w297h666_104.78x234.95mm',
                                                     u'om_w297h666-l_234.95x104.78mm',
                                                     u'om_w277h538_97.72x189.79mm',
                                                     u'om_w277h538-l_189.79x97.72mm',
                                                     u'om_w680h941_239.89x331.96mm',
                                                     u'om_com10_104.78x241.3mm',
                                                     u'om_com10-l_241.3x104.78mm',
                                                     u'om_w315h414_111.13x146.05mm',
                                                     u'om_monarch-l_190.5x98.43mm',
                                                     u'om_w288h387_101.6x136.53mm',
                                                     u'oe_w288h504_4x7in',
                                                     u'om_w288h512_101.6x180.62mm',
                                                     u'om_w253h337_89.25x118.89mm',
                                                     u'om_w155h244_54.68x86.08mm',
                                                     u'om_w155h257_54.68x90.66mm',
                                                     u'om_w283h566_99.84x199.67mm',
                                                     u'custom_min_0.35x0.35mm',
                                                     u'custom_max_297.04x431.8mm'],
                                 'media-top-margin-supported': [353, 635],
                                 'media-type-supported': [u'stationery',
                                                          u'photopaper-pro',
                                                          u'photopaper-plus',
                                                          u'photopaper-plus-double',
                                                          u'photopaper-matte',
                                                          u'photographic-glossy',
                                                          u'stationery-coated',
                                                          u'ink-jet-hagaki',
                                                          u'hagaki',
                                                          u'tshirt',
                                                          u'transparency',
                                                          u'envelope',
                                                          u'photopaper-other'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en-us',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'dbus',
                                                              u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          14,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          56,
                                                          57,
                                                          59,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'output-bin-default': u'face-down',
                                 'output-bin-supported': [u'face-down'],
                                 'output-mode-default': u'color',
                                 'output-mode-supported': [u'monochrome',
                                                           u'color'],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 1,
                                 'pages-per-minute-color': 1,
                                 'pdf-k-octets-supported': (0, 24752472),
                                 'pdf-versions-supported': [u'adobe-1.2',
                                                            u'adobe-1.3',
                                                            u'adobe-1.4',
                                                            u'adobe-1.5',
                                                            u'adobe-1.6',
                                                            u'adobe-1.7',
                                                            u'iso-19005-1_2005',
                                                            u'iso-32000-1_2008',
                                                            u'pwg-5102.3'],
                                 'pdl-override-supported': [u'attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'print-color-mode-default': u'color',
                                 'print-color-mode-supported': [u'monochrome',
                                                                u'color'],
                                 'print-quality-default': 4,
                                 'print-quality-supported': [4, 5],
                                 'printer-commands': u'none',
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-dns-sd-name': None,
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-icons': u'http://localhost:631/icons/Canon-iP90.png',
                                 'printer-info': u'Canon iP90',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'schrabbelkiste',
                                 'printer-make-and-model': u'Canon i80 - CUPS+Gutenprint v5.2.8-pre1',
                                 'printer-more-info': u'http://localhost:631/printers/Canon-iP90',
                                 'printer-name': u'Canon-iP90',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-resolution-default': (301, 300, 3),
                                 'printer-resolution-supported': [(601,
                                                                   600,
                                                                   3),
                                                                  (600,
                                                                   600,
                                                                   3),
                                                                  (602,
                                                                   600,
                                                                   3),
                                                                  (603,
                                                                   600,
                                                                   3),
                                                                  (300,
                                                                   300,
                                                                   3),
                                                                  (301,
                                                                   300,
                                                                   3),
                                                                  (604,
                                                                   600,
                                                                   3),
                                                                  (605,
                                                                   600,
                                                                   3),
                                                                  (606,
                                                                   600,
                                                                   3),
                                                                  (607,
                                                                   600,
                                                                   3),
                                                                  (608,
                                                                   600,
                                                                   3)],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 4,
                                 'printer-state-change-time': 1341402692,
                                 'printer-state-message': u'Printing page 1, 35%',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 176140,
                                 'printer-up-time': 1341402812,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/Canon-iP90'],
                                 'printer-uuid': u'urn:uuid:11cf4a9d-390a-3f68-5f9a-022e522a82bd',
                                 'queued-job-count': 1,
                                 'server-is-sharing-printers': False,
                                 'sides-default': u'one-sided',
                                 'sides-supported': [u'one-sided'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none'],
                                 'which-jobs-supported': [u'completed',
                                                          u'not-completed',
                                                          u'aborted',
                                                          u'all',
                                                          u'canceled',
                                                          u'pending',
                                                          u'pending-held',
                                                          u'processing',
                                                          u'processing-stopped']}}
Page 5 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'C0L0': {u'StpInkType': u'RGB'},
                               u'C1L0': {u'StpBrightness': u'None',
                                         u'StpColorCorrection': u'None',
                                         u'StpContrast': u'None',
                                         u'StpFineBrightness': u'None',
                                         u'StpFineContrast': u'None',
                                         u'StpFineSaturation': u'None',
                                         u'StpImageType': u'TextGraphics',
                                         u'StpSaturation': u'None'},
                               u'C1L1': {u'StpBlackDensity': u'None',
                                         u'StpCyanDensity': u'None',
                                         u'StpDensity': u'None',
                                         u'StpDitherAlgorithm': u'None',
                                         u'StpFineBlackDensity': u'None',
                                         u'StpFineCyanDensity': u'None',
                                         u'StpFineDensity': u'None',
                                         u'StpFineMagentaDensity': u'None',
                                         u'StpFineYellowDensity': u'None',
                                         u'StpMagentaDensity': u'None',
                                         u'StpYellowDensity': u'None'},
                               u'C1L2': {u'StpCyanBalance': u'None',
                                         u'StpCyanGamma': u'None',
                                         u'StpFineCyanBalance': u'None',
                                         u'StpFineCyanGamma': u'None',
                                         u'StpFineGamma': u'None',
                                         u'StpFineMagentaBalance': u'None',
                                         u'StpFineMagentaGamma': u'None',
                                         u'StpFineYellowBalance': u'None',
                                         u'StpFineYellowGamma': u'None',
                                         u'StpGamma': u'None',
                                         u'StpMagentaBalance': u'None',
                                         u'StpMagentaGamma': u'None',
                                         u'StpYellowBalance': u'None',
                                         u'StpYellowGamma': u'None'},
                               u'C1L4': {u'StpLinearContrast': u'False'},
                               u'C1L5': {u'StpFineInkLimit': u'None',
                                         u'StpFineLightCyanTrans': u'None',
                                         u'StpFineLightMagentaTrans': u'None',
                                         u'StpFineLightYellowTrans': u'None',
                                         u'StpInkLimit': u'None',
                                         u'StpLightCyanTrans': u'None',
                                         u'StpLightMagentaTrans': u'None',
                                         u'StpLightYellowTrans': u'None'},
                               u'General': {u'ColorModel': u'Gray',
                                            u'InputSlot': u'Auto',
                                            u'MediaType': u'Plain',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'Resolution': u'301x300dpi',
                                            u'StpColorPrecision': u'Normal',
                                            u'StpQuality': u'Standard',
                                            u'StpiShrinkOutput': u'Shrink'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 6 (Local or remote?):
{'printer_is_remote': False}
Page 7 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Canon;CMD:BJL,BJRaster3,BSCCe;SOJ:TXT01;MDL:iP90;CLS:PRINTER;DES:Canon iP90;VER:1.02;STA:10;',
                      'device-info': u'Canon iP90',
                      'device-location': u'',
                      'device-make-and-model': u'Canon iP90'}}
Page 8 (Printer state reasons):
{'printer-state-message': u'Unable to send data to printer.',
 'printer-state-reasons': [u'none']}
Page 9 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'DefaultAuthType': 'Basic',
                          'JobPrivateAccess': 'default',
                          'JobPrivateValues': 'default',
                          'MaxLogSize': '0',
                          'SubscriptionPrivateAccess': 'default',
                          'SubscriptionPrivateValues': 'default',
                          'SystemGroup': 'lpadmin',
                          'WebInterface': 'Yes',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 3872L,
 'error_log_debug_logging_set': True}
Page 10 (Error log fetch):
{'error_log': ['D [04/Jul/2012:13:54:41 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [04/Jul/2012:13:54:41 +0200] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [04/Jul/2012:13:54:41 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [04/Jul/2012:13:54:41 +0200] cupsdAuthorize: No authentication data provided.',
               'D [04/Jul/2012:13:54:41 +0200] cupsdReadClient: 14 1.1 Get-Jobs 1',
               'D [04/Jul/2012:13:54:41 +0200] Get-Jobs ipp://localhost/printers/',
               'D [04/Jul/2012:13:54:41 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [04/Jul/2012:13:54:41 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [04/Jul/2012:13:54:41 +0200] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [04/Jul/2012:13:54:41 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [04/Jul/2012:13:54:41 +0200] cupsdAuthorize: No authentication data provided.',
               'D [04/Jul/2012:13:54:41 +0200] cupsdReadClient: 14 1.1 Get-Jobs 1',
               'D [04/Jul/2012:13:54:41 +0200] Get-Jobs ipp://localhost/printers/',
               'D [04/Jul/2012:13:54:41 +0200] [Job 19] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 20] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 21] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 22] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 23] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 24] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 25] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 26] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 27] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 28] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 29] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 30] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 31] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 32] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 33] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 34] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 35] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 36] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 37] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 38] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 39] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 40] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 41] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 42] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 43] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 44] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 45] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 46] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 47] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 48] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 49] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 50] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 51] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 52] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 53] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 54] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 55] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 56] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 57] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 58] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 59] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 60] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 61] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 62] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 63] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 64] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 65] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 66] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 67] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 68] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 69] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 70] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] [Job 71] Loading attributes...',
               'D [04/Jul/2012:13:54:41 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [04/Jul/2012:13:54:41 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [04/Jul/2012:13:54:42 +0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1',
               'D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [04/Jul/2012:13:54:42 +0200] cupsdAuthorize: No authentication data provided.',
               'D [04/Jul/2012:13:54:42 +0200] cupsdIsAuthorized: username=""',
               'D [04/Jul/2012:13:54:42 +0200] cupsdSendHeader: 14 WWW-Authenticate: Basic realm="CUPS", trc="y"',
               'D [04/Jul/2012:13:54:42 +0200] cupsdCloseClient: 14',
               'D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [04/Jul/2012:13:54:42 +0200] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [04/Jul/2012:13:54:42 +0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1',
               'D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [04/Jul/2012:13:54:42 +0200] cupsdAuthorize: Authorized as morri using PeerCred',
               'D [04/Jul/2012:13:54:42 +0200] cupsdIsAuthorized: username="morri"',
               'D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [04/Jul/2012:13:54:42 +0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1',
               'D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [04/Jul/2012:13:54:42 +0200] cupsdAuthorize: Authorized as morri using PeerCred',
               'D [04/Jul/2012:13:54:42 +0200] cupsdIsAuthorized: username="morri"',
               'D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [04/Jul/2012:13:54:42 +0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1',
               'D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [04/Jul/2012:13:54:42 +0200] cupsdAuthorize: Authorized as morri using PeerCred',
               'D [04/Jul/2012:13:54:42 +0200] cupsdIsAuthorized: username="morri"',
               'D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [04/Jul/2012:13:54:42 +0200] cupsdReadClient: 14 PUT /admin/conf/cupsd.conf HTTP/1.1',
               'D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [04/Jul/2012:13:54:42 +0200] cupsdAuthorize: Authorized as morri using PeerCred',
               'D [04/Jul/2012:13:54:42 +0200] cupsdIsAuthorized: username="morri"',
               'I [04/Jul/2012:13:54:42 +0200] Installing config file "/etc/cups/cupsd.conf"...',
               'D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [04/Jul/2012:13:54:42 +0200] cupsdCloseClient: 14',
               'D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"',
               'I [04/Jul/2012:13:54:42 +0200] Generating printcap /var/run/cups/printcap...',
               'D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"',
               "W [04/Jul/2012:13:54:42 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-iP90-Gray..' already exists",
               "W [04/Jul/2012:13:54:42 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-iP90-RGB..' already exists",
               "W [04/Jul/2012:13:54:42 +0200] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-iP90' already exists"],
 'error_log_debug_logging_unset': True}
Page 11 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_GB',
 'user_locale_messages': 'en_GB'}

```

```
D [04/Jul/2012:13:54:41 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [04/Jul/2012:13:54:41 +0200] cupsdReadClient: 14 POST / HTTP/1.1
D [04/Jul/2012:13:54:41 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [04/Jul/2012:13:54:41 +0200] cupsdAuthorize: No authentication data provided.
D [04/Jul/2012:13:54:41 +0200] cupsdReadClient: 14 1.1 Get-Jobs 1
D [04/Jul/2012:13:54:41 +0200] Get-Jobs ipp://localhost/printers/
D [04/Jul/2012:13:54:41 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [04/Jul/2012:13:54:41 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [04/Jul/2012:13:54:41 +0200] cupsdReadClient: 14 POST / HTTP/1.1
D [04/Jul/2012:13:54:41 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [04/Jul/2012:13:54:41 +0200] cupsdAuthorize: No authentication data provided.
D [04/Jul/2012:13:54:41 +0200] cupsdReadClient: 14 1.1 Get-Jobs 1
D [04/Jul/2012:13:54:41 +0200] Get-Jobs ipp://localhost/printers/
D [04/Jul/2012:13:54:41 +0200] [Job 19] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 20] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 21] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 22] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 23] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 24] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 25] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 26] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 27] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 28] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 29] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 30] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 31] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 32] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 33] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 34] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 35] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 36] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 37] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 38] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 39] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 40] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 41] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 42] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 43] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 44] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 45] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 46] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 47] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 48] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 49] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 50] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 51] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 52] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 53] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 54] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 55] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 56] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 57] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 58] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 59] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 60] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 61] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 62] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 63] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 64] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 65] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 66] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 67] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 68] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 69] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 70] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] [Job 71] Loading attributes...
D [04/Jul/2012:13:54:41 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [04/Jul/2012:13:54:41 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [04/Jul/2012:13:54:42 +0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [04/Jul/2012:13:54:42 +0200] cupsdAuthorize: No authentication data provided.
D [04/Jul/2012:13:54:42 +0200] cupsdIsAuthorized: username=""
D [04/Jul/2012:13:54:42 +0200] cupsdSendHeader: 14 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [04/Jul/2012:13:54:42 +0200] cupsdCloseClient: 14
D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [04/Jul/2012:13:54:42 +0200] cupsdAcceptClient: 14 from localhost (Domain)
D [04/Jul/2012:13:54:42 +0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [04/Jul/2012:13:54:42 +0200] cupsdAuthorize: Authorized as morri using PeerCred
D [04/Jul/2012:13:54:42 +0200] cupsdIsAuthorized: username="morri"
D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [04/Jul/2012:13:54:42 +0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [04/Jul/2012:13:54:42 +0200] cupsdAuthorize: Authorized as morri using PeerCred
D [04/Jul/2012:13:54:42 +0200] cupsdIsAuthorized: username="morri"
D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [04/Jul/2012:13:54:42 +0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [04/Jul/2012:13:54:42 +0200] cupsdAuthorize: Authorized as morri using PeerCred
D [04/Jul/2012:13:54:42 +0200] cupsdIsAuthorized: username="morri"
D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [04/Jul/2012:13:54:42 +0200] cupsdReadClient: 14 PUT /admin/conf/cupsd.conf HTTP/1.1
D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [04/Jul/2012:13:54:42 +0200] cupsdAuthorize: Authorized as morri using PeerCred
D [04/Jul/2012:13:54:42 +0200] cupsdIsAuthorized: username="morri"
I [04/Jul/2012:13:54:42 +0200] Installing config file "/etc/cups/cupsd.conf"...
D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [04/Jul/2012:13:54:42 +0200] cupsdCloseClient: 14
D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
I [04/Jul/2012:13:54:42 +0200] Generating printcap /var/run/cups/printcap...
D [04/Jul/2012:13:54:42 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
W [04/Jul/2012:13:54:42 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-iP90-Gray..' already exists
W [04/Jul/2012:13:54:42 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-iP90-RGB..' already exists
W [04/Jul/2012:13:54:42 +0200] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-iP90' already exists
E [04/Jul/2012:13:58:36 +0200] [Job 72] Stopping unresponsive job!
W [04/Jul/2012:13:59:33 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-iP90-Gray..' already exists
W [04/Jul/2012:13:59:33 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-iP90-RGB..' already exists
W [04/Jul/2012:13:59:33 +0200] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-iP90' already exists
I [04/Jul/2012:13:59:46 +0200] Remote access is disabled.
D [04/Jul/2012:13:59:46 +0200] Added auto ServerAlias schrabbelkiste
I [04/Jul/2012:13:59:46 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [04/Jul/2012:13:59:46 +0200] Using default TempDir of /var/spool/cups/tmp...
I [04/Jul/2012:13:59:46 +0200] Configured for up to 100 clients.
I [04/Jul/2012:13:59:46 +0200] Allowing up to 100 client connections per host.
I [04/Jul/2012:13:59:46 +0200] Using policy "default" as the default.
D [04/Jul/2012:13:59:46 +0200] load_ppd: Loading /var/cache/cups/Canon-iP90.data...
D [04/Jul/2012:13:59:46 +0200] Calling DeleteDevice(cups-Canon-iP90)
D [04/Jul/2012:13:59:46 +0200] failed to DeleteDevice: org.freedesktop.DBus.Error.InvalidArgs:Type of message, `(s)', does not match expected type `(o)'
D [04/Jul/2012:13:59:46 +0200] Using profile id of Canon-iP90-Gray..
D [04/Jul/2012:13:59:46 +0200] Calling CreateProfile(Canon-iP90-Gray..,temp)
W [04/Jul/2012:13:59:46 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-iP90-Gray..' already exists
D [04/Jul/2012:13:59:46 +0200] Using profile id of Canon-iP90-RGB..
D [04/Jul/2012:13:59:46 +0200] Calling CreateProfile(Canon-iP90-RGB..,temp)
W [04/Jul/2012:13:59:46 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-iP90-RGB..' already exists
I [04/Jul/2012:13:59:46 +0200] Registering ICC color profiles for "Canon-iP90"
D [04/Jul/2012:13:59:46 +0200] Calling CreateDevice(cups-Canon-iP90,temp)
W [04/Jul/2012:13:59:46 +0200] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-iP90' already exists
D [04/Jul/2012:13:59:46 +0200] cupsdRegisterPrinter(p=0x228c19a0(Canon-iP90))
D [04/Jul/2012:13:59:46 +0200] cupsdMarkDirty(---p--)
D [04/Jul/2012:13:59:46 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs"
I [04/Jul/2012:13:59:46 +0200] Partial reload complete.
I [04/Jul/2012:13:59:46 +0200] Listening to [v1.::1]:631 on fd 9...
I [04/Jul/2012:13:59:46 +0200] Listening to 127.0.0.1:631 on fd 10...
I [04/Jul/2012:13:59:46 +0200] Listening to /var/run/cups/cups.sock:631 on fd 11...
I [04/Jul/2012:13:59:46 +0200] Resuming new connection processing...
D [04/Jul/2012:13:59:46 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
D [04/Jul/2012:13:59:46 +0200] Discarding unused server-restarted event...
D [04/Jul/2012:13:59:46 +0200] [Job 72] Read 222 bytes of back-channel data...
D [04/Jul/2012:13:59:46 +0200] Report: clients=0
D [04/Jul/2012:13:59:46 +0200] Report: jobs=54
D [04/Jul/2012:13:59:46 +0200] Report: jobs-active=1
D [04/Jul/2012:13:59:46 +0200] Report: printers=1
D [04/Jul/2012:13:59:46 +0200] Report: printers-implicit=0
D [04/Jul/2012:13:59:46 +0200] Report: stringpool-string-count=23392
D [04/Jul/2012:13:59:46 +0200] Report: stringpool-alloc-bytes=22512
D [04/Jul/2012:13:59:46 +0200] Report: stringpool-total-bytes=433800
D [04/Jul/2012:13:59:47 +0200] [Job 72] Read 222 bytes of back-channel data...
D [04/Jul/2012:13:59:47 +0200] cupsdAcceptClient: 14 from localhost (Domain)
D [04/Jul/2012:13:59:48 +0200] [Job 72] Read 222 bytes of back-channel data...
D [04/Jul/2012:13:59:49 +0200] [Job 72] Read 222 bytes of back-channel data...
D [04/Jul/2012:13:59:49 +0200] cupsdReadClient: 14 POST / HTTP/1.1
D [04/Jul/2012:13:59:49 +0200] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [04/Jul/2012:13:59:49 +0200] cupsdAuthorize: No authentication data provided.
D [04/Jul/2012:13:59:49 +0200] cupsdReadClient: 14 1.1 Get-Jobs 1
D [04/Jul/2012:13:59:49 +0200] Get-Jobs ipp://localhost/printers/
D [04/Jul/2012:13:59:49 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [04/Jul/2012:13:59:49 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [04/Jul/2012:13:59:49 +0200] cupsdReadClient: 14 POST / HTTP/1.1
D [04/Jul/2012:13:59:49 +0200] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [04/Jul/2012:13:59:49 +0200] cupsdAuthorize: No authentication data provided.
D [04/Jul/2012:13:59:49 +0200] cupsdReadClient: 14 1.1 Get-Jobs 1
D [04/Jul/2012:13:59:49 +0200] Get-Jobs ipp://localhost/printers/
D [04/Jul/2012:13:59:49 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [04/Jul/2012:13:59:49 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [04/Jul/2012:13:59:49 +0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [04/Jul/2012:13:59:49 +0200] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [04/Jul/2012:13:59:49 +0200] cupsdAuthorize: No authentication data provided.
D [04/Jul/2012:13:59:49 +0200] cupsdIsAuthorized: username=""
D [04/Jul/2012:13:59:49 +0200] cupsdSendHeader: 14 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [04/Jul/2012:13:59:49 +0200] cupsdCloseClient: 14
D [04/Jul/2012:13:59:49 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [04/Jul/2012:13:59:49 +0200] cupsdAcceptClient: 14 from localhost (Domain)
D [04/Jul/2012:13:59:49 +0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [04/Jul/2012:13:59:49 +0200] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [04/Jul/2012:13:59:49 +0200] cupsdAuthorize: Authorized as morri using PeerCred
D [04/Jul/2012:13:59:49 +0200] cupsdIsAuthorized: username="morri"
D [04/Jul/2012:13:59:49 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [04/Jul/2012:13:59:49 +0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [04/Jul/2012:13:59:49 +0200] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [04/Jul/2012:13:59:49 +0200] cupsdAuthorize: Authorized as morri using PeerCred
D [04/Jul/2012:13:59:49 +0200] cupsdIsAuthorized: username="morri"
D [04/Jul/2012:13:59:49 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [04/Jul/2012:13:59:49 +0200] cupsdReadClient: 14 GET /admin/conf/cupsd.conf HTTP/1.1
D [04/Jul/2012:13:59:49 +0200] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [04/Jul/2012:13:59:49 +0200] cupsdAuthorize: Authorized as morri using PeerCred
D [04/Jul/2012:13:59:49 +0200] cupsdIsAuthorized: username="morri"
D [04/Jul/2012:13:59:49 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [04/Jul/2012:13:59:49 +0200] cupsdReadClient: 14 PUT /admin/conf/cupsd.conf HTTP/1.1
D [04/Jul/2012:13:59:49 +0200] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Printing jobs and dirty files"
D [04/Jul/2012:13:59:49 +0200] cupsdAuthorize: Authorized as morri using PeerCred
D [04/Jul/2012:13:59:49 +0200] cupsdIsAuthorized: username="morri"
I [04/Jul/2012:13:59:49 +0200] Installing config file "/etc/cups/cupsd.conf"...
D [04/Jul/2012:13:59:50 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
D [04/Jul/2012:13:59:50 +0200] cupsdCloseClient: 14
D [04/Jul/2012:13:59:50 +0200] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Printing jobs and dirty files"
I [04/Jul/2012:13:59:50 +0200] Generating printcap /var/run/cups/printcap...
D [04/Jul/2012:13:59:50 +0200] cupsdSetBusyState: newbusy="Printing jobs", busy="Printing jobs and dirty files"
W [04/Jul/2012:13:59:50 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-iP90-Gray..' already exists
W [04/Jul/2012:13:59:50 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-iP90-RGB..' already exists
W [04/Jul/2012:13:59:50 +0200] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-iP90' already exists
```

---

