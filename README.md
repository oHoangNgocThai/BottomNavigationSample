# BottomNavigationSample

# BottomNavigation Basic

## Overview

## Create BottomNavigation

* Để tạo giao diện cho BottomNavigation, trước hết hãy thiết kế trong layout với widget **BottomNavigationView**.

```
<android.support.design.widget.BottomNavigationView
        android:id="@+id/navigation"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="0dp"
        android:layout_marginEnd="0dp"
        android:background="?android:attr/windowBackground"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:menu="@menu/navigation" />
```

* Sau đó chú ý đến tạo một menu để thêm vào trong thuộc tính **app:menu** của BottomNavigation.

```
<menu xmlns:android="http://schemas.android.com/apk/res/android">

    <item
        android:id="@+id/navigation_home"
        android:icon="@drawable/ic_home_black_24dp"
        android:title="@string/title_home" />

    <item
        android:id="@+id/navigation_dashboard"
        android:icon="@drawable/ic_dashboard_black_24dp"
        android:title="@string/title_dashboard" />

    <item
        android:id="@+id/navigation_notifications"
        android:icon="@drawable/ic_notifications_black_24dp"
        android:title="@string/title_notifications" />

</menu>
```

* Lắng nghe sự kiện click vào các tab của BottomNavigation sử dụng **OnNavigationItemSelectedListener**.

```
private val mOnNavigationItemSelectedListener = BottomNavigationView.OnNavigationItemSelectedListener { item ->
    when (item.itemId) {
        R.id.navigation_home -> {
            putFragment(HomeFragment.newInstance())
            return@OnNavigationItemSelectedListener true
        }
        R.id.navigation_dashboard -> {
            putFragment(DashboardFragment.newInstance())
            return@OnNavigationItemSelectedListener true
        }
        R.id.navigation_notifications -> {
            putFragment(NotificationFragment.newInstance())
            return@OnNavigationItemSelectedListener true
        }
    }
    false
}
```

* Có thể thay đổi màu mặc định của các icon và text của chúng theo ý thích khi được select hoặc là bình thường sử dụng color.

```
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:color="#F30202" android:state_checked="true" />
    <item android:color="#757575" android:state_checked="false" />
</selector>

// Apply
app:itemIconTint="@color/color_tab"
app:itemTextColor="@color/color_tab"

```

* Bạn cũng có thể sử dụng phương thức **inflateMenu** để có thể thêm menu khác vào đối với từng loại người dùng chứ không phải là fix cứng.

```
navigation.inflateMenu(R.menu.navigation_simple)
```

* Thay icon của menu bên trong BottomNavigation, chúng ta sử dụng menu được lấy ra rồi set 1 icon khác vào.

```
navigation.menu.findItem(R.id.navigation_home).setIcon(R.drawable.ic_android_black_24dp)
```

# Custom BottomNavigation

# BottomNavigation with Navigation Component
