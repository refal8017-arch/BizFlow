# BizFlow
BizFlow منصة رقمية تساعد أصحاب الأعمال على تنظيم الحجوزات والتواصل مع العملاء بدل الاعتماد على الواتساب، من خلال إدارة الخدمات والطلبات في مكان واحد لتحسين الكفاءة وتوفير الوقت
BizFlow
وصف المشروع
BizFlow منصة رقمية تساعد أصحاب الأعمال على تنظيم الحجوزات والتواصل مع العملاء بدل الاعتماد على الواتساب، من خلال إدارة الخدمات والطلبات في مكان واحد لتحسين الكفاءة وتوفير الوقت

المميزات
إدارة وتنظيم المواعيد  
عرض الخدمات والأسعار  
نظام حجز سهل وسريع  
تنبيهات بالمواعيد  


طريقة التشغيل
1. تحميل المشروع  
2. فتح ملفات المشروع  
3. تشغيل التطبيق أو الموقع حسب البيئة المستخدمة  

فريق العمل
- لانا حسن، رغد الزهراني (التطبيق)  
- لين آل صامع (قاعدة البيانات)  
- ريفال المولد، غلا القليطي (الموقع)  
- حلا المالكي، جنى الجهني (البرمجة Backend)  

الليدر
- غلا
import { StyleSheet, Platform, Dimensions } from 'react-native';

const { width: screenWidth, height: screenHeight } = Dimensions.get('window');

// حساب العرض الذهبي للأعمدة لضمان التناسق التام في لوحة Trello
const TOTAL_CARDS_WIDTH = screenWidth - 30;
const GAP_BETWEEN_CARDS = 8; 
const FINAL_COLUMN_WIDTH = (TOTAL_CARDS_WIDTH / 2) - (GAP_BETWEEN_CARDS / 2);

export const styles = StyleSheet.create({
  container: { 
    flex: 1, 
    backgroundColor: '#f5f2ee' 
  },
  
  // --- الهيدر العلوي ---
  stickyHeader: {
    position: 'absolute',
    top: 0, left: 0, right: 0,
    height: 115, 
    backgroundColor: '#ffffff',
    zIndex: 1000,
    elevation: 5,
    shadowColor: '#000',
    shadowOffset: { width: 0, height: 3 },
    shadowOpacity: 0.12,
    shadowRadius: 5,
    paddingTop: Platform.OS === 'ios' ? 45 : 15,
  },
  headerTop: {
    flexDirection: 'row', 
    justifyContent: 'space-between',
    alignItems: 'center',
    paddingHorizontal: 20,
    marginBottom: 10,
  },
  headerCenter: { flex: 1, alignItems: 'center', justifyContent: 'center' },
  navLogoSmall: { width: 100, height: 40, resizeMode: 'contain' },
  navSettingsBtn: { padding: 5 },

  // أزرار التنقل السريع
  quickNav: {
    flexDirection: 'row-reverse',
    justifyContent: 'center',
    paddingBottom: 10,
  },
  navItem: {
    paddingVertical: 6,
    paddingHorizontal: 14,
    marginHorizontal: 5,
    borderRadius: 20,
    backgroundColor: '#f5f2ee',
    borderWidth: 1,
    borderColor: 'rgba(63, 64, 60, 0.08)',
  },
  navItemText: { fontSize: 11, fontWeight: '700', color: '#3f403c' },

  // --- الكروت الرئيسية ---
  card: { 
    backgroundColor: '#ffffff', 
    marginHorizontal: 15, 
    marginVertical: 8, 
    padding: 20, 
    borderRadius: 22, 
    borderWidth: 1,
    borderColor: 'rgba(63, 64, 60, 0.05)',
    elevation: 3,
  },

  // --- قسم الإحصائيات (تم حذف النسب تماماً) ---
  statsGrid: {
    flexDirection: 'row-reverse',
    justifyContent: 'space-between',
    width: '100%',
    marginTop: 5,
  },
  statItem: {
    flex: 1,
    marginHorizontal: 4,
    alignItems: 'center',
    justifyContent: 'center',
    paddingVertical: 14,
    backgroundColor: '#faf9f7',
    borderRadius: 16,
    borderWidth: 1,
    borderColor: 'rgba(63, 64, 60, 0.04)',
  },
  statNumber: { 
    fontSize: 20, 
    fontWeight: '900', 
    color: '#3f403c' 
  },
  
  statFooter: {
    flexDirection: 'row-reverse', 
    alignItems: 'center',
    justifyContent: 'center',
    marginTop: 4,
    width: '100%'
  },
  statLabel: { 
    fontSize: 9, 
    color: '#71726e', 
    fontWeight: '700', 
    textAlign: 'center' 
  },

  // --- لوحة الحجوزات Trello ---
  trelloColumn: {
    width: FINAL_COLUMN_WIDTH,
    borderRadius: 20,
    marginHorizontal: GAP_BETWEEN_CARDS / 2,
    padding: 12,
    height: screenHeight * 0.6, 
    borderWidth: 1,
    backgroundColor: '#ffffff',
  },

  pendingColumn: { backgroundColor: 'rgba(243, 156, 18, 0.02)', borderColor: 'rgba(243, 156, 18, 0.12)' },
  urgentColumn: { backgroundColor: 'rgba(231, 76, 60, 0.02)', borderColor: 'rgba(231, 76, 60, 0.22)', borderWidth: 1.5 },
  confirmedColumn: { backgroundColor: 'rgba(63, 64, 60, 0.02)', borderColor: 'rgba(63, 64, 60, 0.12)' },
  completedColumn: { backgroundColor: 'rgba(46, 204, 113, 0.02)', borderColor: 'rgba(46, 204, 113, 0.12)' },

  columnHeader: {
    paddingVertical: 10,
    borderRadius: 12,
    marginBottom: 15,
    alignItems: 'center',
    justifyContent: 'center',
    minHeight: 40,
  },
  columnHeaderText: { color: '#3f403c', fontWeight: '800', fontSize: 11 },
  columnHeaderCount: {
    position: 'absolute',
    right: 8,
    fontSize: 10,
    fontWeight: '900',
    color: '#3f403c',
    backgroundColor: 'rgba(255,255,255,0.8)',
    paddingHorizontal: 6,
    borderRadius: 6,
  },
  
  pendingHeader: { backgroundColor: 'rgba(243, 156, 18, 0.18)' },
  urgentHeader: { backgroundColor: 'rgba(231, 76, 60, 0.18)' },
  confirmedHeader: { backgroundColor: 'rgba(63, 64, 60, 0.12)' },
  completedHeader: { backgroundColor: 'rgba(46, 204, 113, 0.18)' },
// --- كروت الحجوزات ---
  trelloCardPending: {
    backgroundColor: '#ffffff', padding: 14, borderRadius: 14, marginBottom: 12, borderWidth: 1.5, borderColor: 'rgba(243, 156, 18, 0.35)', elevation: 2,
  },
  trelloCardConfirmed: {
    backgroundColor: '#ffffff', padding: 14, borderRadius: 14, marginBottom: 12, borderWidth: 1.5, borderColor: 'rgba(63, 64, 60, 0.25)', elevation: 2,
  },
  trelloCardCompleted: {
    backgroundColor: '#ffffff', padding: 14, borderRadius: 14, marginBottom: 12, borderWidth: 1.5, borderColor: 'rgba(46, 204, 113, 0.35)', elevation: 2,
  },
  trelloCardUrgent: {
    backgroundColor: '#ffffff', padding: 14, borderRadius: 14, marginBottom: 12, borderWidth: 2, borderColor: '#e74c3c', elevation: 4,
  },

  cardName: { fontWeight: '800', fontSize: 14, color: '#3f403c', textAlign: 'right', marginBottom: 4 },
  customerPhone: { fontSize: 11, color: '#71726e', fontWeight: '600', textAlign: 'right', marginBottom: 6 },
  cardInfo: { fontSize: 11, color: '#71726e', textAlign: 'right', lineHeight: 16 },
  cardTime: { fontSize: 10, color: '#e67e22', textAlign: 'right', marginTop: 6, fontWeight: '800' },

  // --- الأزرار ---
  cardActions: { 
    flexDirection: 'row-reverse', 
    justifyContent: 'space-between', 
    marginTop: 12,
    width: '100%',
  },
  btnAcceptSmall: { backgroundColor: '#3f403c', paddingVertical: 9, borderRadius: 8, alignItems: 'center', justifyContent: 'center', flex: 1, marginHorizontal: 2, height: 38 },
  btnDone: { backgroundColor: '#3f403c', paddingVertical: 9, borderRadius: 8, alignItems: 'center', justifyContent: 'center', flex: 1, marginHorizontal: 2, height: 38 },
  btnRejectSmall: { paddingVertical: 9, alignItems: 'center', justifyContent: 'center', flex: 1, borderWidth: 1.5, borderColor: '#e74c3c', borderRadius: 8, marginHorizontal: 2, height: 38 },
  btnTextWhite: { color: '#ffffff', fontSize: 12, fontWeight: '800' },
  btnTextRed: { color: '#e74c3c', fontSize: 12, fontWeight: '800' },

  // --- نصوص وعناصر عامة ---
  title: { fontSize: 22, fontWeight: '900', color: '#3f403c', textAlign: 'center' },
  secTitle: { fontSize: 17, fontWeight: '800', color: '#3f403c', textAlign: 'right' },
  desc: { color: '#71726e', textAlign: 'center', marginTop: 6, fontSize: 14, lineHeight: 20 },
  blueBtn: { color: '#3f403c', fontWeight: '800', fontSize: 12, backgroundColor: '#f5f2ee', paddingVertical: 8, paddingHorizontal: 15, borderRadius: 12, borderWidth: 1, borderColor: 'rgba(63, 64, 60, 0.15)' },
  editLink: { position: 'absolute', top: 15, left: 15, zIndex: 10 },
  divider: { height: 1, backgroundColor: 'rgba(63, 64, 60, 0.08)', marginVertical: 15 },
  center: { alignItems: 'center' },

  // --- الفورم والمودال ---
  addForm: { backgroundColor: '#faf9f7', padding: 18, borderRadius: 18, marginBottom: 15, borderWidth: 1, borderColor: 'rgba(63, 64, 60, 0.06)' },
  smallInput: { height: 45, borderBottomWidth: 1.5, borderColor: 'rgba(63, 64, 60, 0.12)', paddingHorizontal: 10, marginBottom: 12, textAlign: 'right', fontSize: 14, color: '#3f403c' },
  serviceRow: { paddingVertical: 15, borderBottomWidth: 1, borderBottomColor: 'rgba(63, 64, 60, 0.04)' },
modalBack: { flex: 1, backgroundColor: 'rgba(0,0,0,0.6)', justifyContent: 'flex-end' },
  sheet: { backgroundColor: '#fff', padding: 30, borderTopLeftRadius: 35, borderTopRightRadius: 35 },
  sheetHeader: { flexDirection: 'row-reverse', justifyContent: 'space-between', marginBottom: 25, alignItems: 'center' },
  logoutBtn: { padding: 18, alignItems: 'center', backgroundColor: '#3f403c', borderRadius: 16, marginTop: 15 },
  accountBox: { marginBottom: 25, backgroundColor: '#fcfbf9', borderRadius: 18, padding: 8, borderWidth: 1, borderColor: 'rgba(63, 64, 60, 0.05)' },
  accountRow: { flexDirection: 'row-reverse', justifyContent: 'space-between', alignItems: 'center', paddingVertical: 15, paddingHorizontal: 18, borderBottomWidth: 1, borderBottomColor: 'rgba(63, 64, 60, 0.05)' },
  accountLabel: { fontSize: 14, color: '#71726e', fontWeight: '600' },
  accountValue: { fontSize: 14, color: '#3f403c', fontWeight: '800' },
// فورم الموظف
sheetTitle: {
    fontSize: 20, // كبرناه شوي عشان البرستيج
    fontWeight: '700',
    color: '#3f403c',
    textAlign: 'center', // يخلي النص في نص المساحة المتاحة له
    flex: 1, // يخليه يتمدد في النص
  },
  closeText: {
    color: '#e74c3c',
    fontSize: 14,
    fontWeight: '600',
  },
  addStaffBtn: {
    borderWidth: 1,
    borderColor: '#3f403c',
    borderRadius: 12,
    height: 50,
    justifyContent: 'center',
    alignItems: 'center',
    marginTop: 15,
  },
  addStaffBtnText: {
    color: '#3f403c',
    fontWeight: 'bold',
  }


  
});
