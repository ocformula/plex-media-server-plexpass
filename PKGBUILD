# Maintainer: Donald Webster <fryfrog@gmail.com>
# Contributor: Mikael Eriksson <mikael_eriksson@miffe.org>
# Contributor: Maxime Gauduin <alucryd@archlinux.org>
# Contributor: Rob Sletten <rsletten@gmail.com>
# Contributor: Tom Moore <t.moore01@gmail.com>
# Contributor: monty <linksoft@gmx.de>
# Contributor: Jon Wiersma <archaur@jonw.org>
# Contributor: Arthur <arthur.darcet@m4x.org>
# Contributor: Praekon <praekon@googlemail.com>

# Based on the plex-media-server package by Maxime Gauduin.

pkgname=plex-media-server-plexpass
pkgver=1.13.0.5023
_pkgsum=31d3c0c65
pkgrel=1
pkgdesc='Plex Media Server (PlexPass version)'
arch=('armv7h' 'i686' 'x86_64')
url='https://plex.tv/'
license=('custom')
options=('!emptydirs')
provides=('plex-media-server')
conflicts=('plex-media-server')
backup=('etc/conf.d/plexmediaserver')
install='plex-media-server.install'
source=('plexmediaserver.conf.d'
        'plexmediaserver.service'
        'plex.sysusers'
        'plex.tmpfiles'
        'terms.txt')

source_armv7h=("https://downloads.plex.tv/plex-media-server/${pkgver}-${_pkgsum}/PlexMediaServer-${pkgver}-${_pkgsum}-arm7.spk")
source_i686=("https://downloads.plex.tv/plex-media-server/${pkgver}-${_pkgsum}/plexmediaserver-${pkgver}-${_pkgsum}.i386.rpm")
source_x86_64=("https://downloads.plex.tv/plex-media-server/${pkgver}-${_pkgsum}/plexmediaserver-${pkgver}-${_pkgsum}.x86_64.rpm")

sha256sums=('88779d4d04e44de05428754481c2b67a0e2bf47795dce875819bf7308de49025'
            '348075917da3bac9659d047a45c264c556475e66779ecd84cf00d178a5b7bebf'
            'c597bee0bcbb59ed791651555a904e5f7e9d2e82f6c6986b6352e5fc38e5b557'
            'e3c278315bf325d9bddbedbbdb5680791acdc72ce3d4972935ef27b491518ce5'
            '7bb97271eb2dc5d1dcb95f9763f505970d234df17f1b8d79b467b9020257915a')
sha256sums_armv7h=('6a9e5684144cef6df65f3e0c9c6741ef9b03c10a038ddb6877b256aaab9ab10e')
sha256sums_i686=('a80ce8c41debca376a6cabfb3ec406b36382405d35fbcd5c2b42496a6c32ac88')
sha256sums_x86_64=('b94d571bcd47bc3201fd7f54b910f5693cabd1b543d5d0b4705668b7b7c24602')

prepare() {
  if [[ $CARCH = arm* ]]; then
    mkdir -p usr/lib/plexmediaserver
    bsdtar -xf package.tgz -C usr/lib/plexmediaserver/
  fi
}

package() {
  install -d -m 755 "${pkgdir}/usr/lib/plexmediaserver"
  cp -dr --no-preserve='ownership' "${srcdir}/usr/lib/plexmediaserver" "${pkgdir}/usr/lib/"

  install -D -m 644 "${srcdir}/plexmediaserver.conf.d" "${pkgdir}/etc/conf.d/plexmediaserver"
  install -D -m 644 "${srcdir}/plexmediaserver.service" "${pkgdir}/usr/lib/systemd/system/plexmediaserver.service"
  install -D -m 644 "${srcdir}/plex.sysusers" "${pkgdir}/usr/lib/sysusers.d/plex.conf"
  install -D -m 644 "${srcdir}/plex.tmpfiles" "${pkgdir}/usr/lib/tmpfiles.d/plex.conf"

  install -D -m 644 "${srcdir}/terms.txt" "${pkgdir}/usr/share/licenses/${pkgname}/terms.txt"
}

# vim: ts=2 sw=2 et:
