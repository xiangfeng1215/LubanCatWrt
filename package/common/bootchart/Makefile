#
# Copyright (C) 2019 Zengxiangfeng <zengxiangfeng@cvte.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=bootchart
PKG_RELEASE:=1

#PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/bootchart
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Utility for get router message.
  MAINTAINER:=zengxiangfeng <zengxiangfeng@cvte.com>
endef

define Package/bootchart/description
 This package contains an utility that bootchart .
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		CC="$(TARGET_CC)" \
		CFLAGS="$(TARGET_CFLAGS) -Wall"
endef

define Package/bootchart/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/sbin/

	$(INSTALL_BIN) $(PKG_BUILD_DIR)/bootchart-lite $(1)/sbin/
	$(CP) ./files/* $(1)/

endef

$(eval $(call BuildPackage,bootchart))
