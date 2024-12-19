# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Daniel Bermond <dbermond@archlinux.org>

_pkg=aribcaption
pkgname="lib${_pkg}"
pkgver=1.1.1
pkgrel=1
_pkgdesc=(
  "Caption decoder/renderer library"
  "for handling ARIB STD-B24 based"
  "TV broadcast captions"
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'x86_64'
  'i686'
  'arm'
  'aarch64'
  'armv7l'
  'armv6l'
  'pentium4'
  'mips'
  'powerpc'
)
_http="https://github.com"
_ns="xqq"
url="${_http}/${_ns}/${pkgname}"
license=(
  'MIT'
)
depends=(
  'fontconfig'
  'freetype2'
)
makedepends=(
  'cmake'
)
source=(
  "${url}/archive/v${pkgver}/${pkgname}-${pkgver}.tar.gz"
)
sha256sums=(
  '278d03a0a662d00a46178afc64f32535ede2d78c603842b6fd1c55fa9cd44683'
)

build() {
  local \
    _cmake_opts=()
  _cmake_opts=(
    -DCMAKE_BUILD_TYPE:STRING='None'
    -DCMAKE_INSTALL_PREFIX:PATH='/usr'
    -DARIBCC_SHARED_LIBRARY:BOOL='ON'
    -Wno-dev
  )
  cmake \
    -B \
      build \
    -S \
      "${pkgname}-${pkgver}" \
    -G \
      'Unix Makefiles' \
    "${_cmake_opts[@]}"
  cmake \
    --build \
      build
}

package() {
  DESTDIR="${pkgdir}" \
  cmake \
    --install \
      build
  install \
    -Dm644 \
    "${pkgname}-${pkgver}/LICENSE" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}"
}
