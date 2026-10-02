SERVICEDIR=$(DESTDIR)/lib/systemd/system

all:
	@true

# 'lsbservice' (see debian/rules and the pkg.pve-network.lsbservice build
# profile) skips the systemd drop-in, which has no meaning without systemd
PVE_INIT_SYSTEM ?= systemd
ifeq ($(filter $(PVE_INIT_SYSTEM),systemd lsbservice),)
$(error unsupported PVE_INIT_SYSTEM '$(PVE_INIT_SYSTEM)' (expected 'systemd' or 'lsbservice'))
endif

.PHONY: install
install:
ifneq ($(PVE_INIT_SYSTEM),lsbservice)
	install -d $(SERVICEDIR)
	install -d $(SERVICEDIR)/dnsmasq@.service.d
	install -t $(SERVICEDIR)/dnsmasq@.service.d -m 0644 00-dnsmasq-after-networking.conf
endif

.PHONY: clean
clean:
	@true
