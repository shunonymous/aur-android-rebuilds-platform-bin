# Maintainer: shunonymous
# Contributor: goetzc
# Contributor: Skycoder42
# Contributor: Kppqju77
# Contributor: lestb
# Contributor: Philipp Wolfer
# Contributor: Joel Pedraza
# Contributor: Jakub Schmidtke

_pkgname=android-platform
pkgname=android-rebuilds-platform-bin
_apilevel=30
_rev=r03
pkgver=${_apilevel}_${_rev}
pkgrel=1
pkgdesc="Android SDK Platform, latest API"
arch=('any')
url="https://android-rebuilds.beuc.net/"
license=('custom')
provides=("android-platform" "${_pkgname}-${_apilevel}")
conflicts=("${_pkgname}-${_apilevel}")
options=('!strip')
source=("https://android-rebuilds.beuc.net/dl/repository/sdk-repo-linux-platforms-eng.11.0.0_r27.zip"
        "https://android-rebuilds.beuc.net/dl/repository/repository-11.0.0_r27.xml")
sha1sums=('e1edf347d3a19c54f0a2f84f0bf6a1ad16089e18'
          'd69d96c0384b6682090bc22a70a1fec4cfe5c43c')
sha384sums=('1f64baec7e46b5cef3198df5c760f3bb623286330362e6c2fdb07c395f27fadfdfb0c2871d5a67777c29e3c938dff032'
            'a4d09072476b85379c243d97a0b4add9c1c581f94dc6004729174382824ff76641c1d22a586c539e3f81235896dafd0a')

package() {
  depends=('android-sdk' 'android-sdk-platform-tools')
  
  mkdir -p "${pkgdir}/opt/android-sdk/platforms/"
  install -D -m 644 "${srcdir}/android-11/data/NOTICE.txt" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
  find "${srcdir}" -maxdepth 1 -mindepth 1 -type d | grep -P 'android-[0-9]+(\.[0-9]*)*$' | while read directory; do
      mv "${directory}" "${pkgdir}/opt/android-sdk/platforms/android-${_apilevel}"
  done

  chmod -R ugo+rX "${pkgdir}/opt"
}
